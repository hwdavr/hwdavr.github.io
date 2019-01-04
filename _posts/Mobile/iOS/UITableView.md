---


---

<h3 id="flickering-issue-when-reload-data">Flickering issue when reload data</h3>
<p>As you have guessed, flickering is caused by calling [self.tableView reloadData]; rapidly and repeatedly, especially on iOS 5.x devices. But you probably do not want to reload the entire table, you want to update just the view within the visible cells of the table.</p>
<p>Let’s say you want to update each cell of a table to reflect the latest download % as a file is downloading. A method [downloading:totalRead:totalExpected:] gets called in my example, extremely rapidly as bytes are downloading.</p>
<p>This is what  <strong>NOT</strong>  to do… reload the table on every little update (in this example, the developer may rely on “cellForRowAtIndexPath” or “willDisplayCell” methods perform the updating of all the visible cells):</p>
<pre><code>    - (void)downloading:(PPFile *)file totalRead:(long long)read totalExpected:(long long)expected {
        // Bad! Causes flickering when rapidly executed:
        [self.tableView reloadData];
    }
</code></pre>
<p>The following is a better solution. When a cell’s view needs to be updated, find that cell by grabbing only the visible cells from the table, and then update that cell’s view directly without reloading the table:</p>
<pre><code>    - (void)downloading:(PPFile *)file totalRead:(long long)read totalExpected:(long long)expected {
        NSArray *cells = [self.tableView visibleCells];

        for(MYCellView *cell in cells) {
            if(cell.fileReference == file) {
                // Update your cell's view here.
            }
        }
    }
</code></pre>

