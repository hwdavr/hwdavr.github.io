---


---

<h3 id="implementation">Implementation</h3>
<p><a href="https://github.com/sepulo/globalplatform.net">https://github.com/sepulo/globalplatform.net</a></p>
<h3 id="samsung-wallet-tsm-solution">Samsung Wallet TSM solution</h3>
<p><a href="https://www.blackhat.com/docs/eu-17/materials/eu-17-Ma-How-Samsung-Secures-Your-Wallet-And-How-To-Break-It.pdf">https://www.blackhat.com/docs/eu-17/materials/eu-17-Ma-How-Samsung-Secures-Your-Wallet-And-How-To-Break-It.pdf</a><br>
Registration-SE Operations</p>
<ul>
<li>Create Supplementary Security Domain:<br>
•Done by SKMS Agent and Samsung Server;<br>
•Use Keyisd to set up Secure Channel, encrypted by Triple DES;<br>
•Only Samsung and SE know Key<sub>isd</sub>;<br>
•Working in privilege Security Domain—Issuer Security Domain;<br>
•At the end of this stage, Key<sub>default</sub> is set for new domain;</li>
<li>Update Supplementary Security Domain (SSD) keys:<br>
•Update Key<sub>default</sub> with Key<sub>bank</sub>;<br>
•Working in supplementary Security Domain;</li>
<li>Install ARC-C Application:<br>
•ARA-C( Access Rule Application Client);<br>
•Hardware-based Access Control Mechanism, allow specific android app to access SE;<br>
•Hash of certificate is written into;</li>
<li>Personalize AMSD and Write SEID:<br>
•AMSD(Authorized Mode Secured Domain, AMSD);<br>
•Bank assigns an SEID for SE, and write it into SE;</li>
<li>Add Access Rules for CRS:<br>
•CRS(Contactless Registry Service)<br>
•Application selection rules on the contactless interface(for NFC);</li>
<li>Install CARDS Applet:
<ul>
<li>Seems Core of Bank implementation,around 11K;</li>
<li>After Installation, few initializaiton opertions are done by ISO7816 standard cmds instead of secure channel:<br>
•CREATE FILE<br>
•UPDATE BINARY<br>
•GET CHALLENGE<br>
•SET PIN</li>
</ul>
</li>
</ul>
<h3 id="secure-channel-protocol">Secure Channel Protocol</h3>
<p><a href="http://naeemgik.blogspot.com/2017/12/globalplatform-secure-channel-protocol.html">http://naeemgik.blogspot.com/2017/12/globalplatform-secure-channel-protocol.html</a>?<em>sm_au</em>=iMHvFVnFkJ17ksQ5<br>
<a href="https://pdfs.semanticscholar.org/2ee2/ebe1a1cf2536eb487e9be0a976cb55f41199.pdf">https://pdfs.semanticscholar.org/2ee2/ebe1a1cf2536eb487e9be0a976cb55f41199.pdf</a><br>
A Security Domain, including the Issuer Security Domain shall have at least one key set containing 3 keys to be used in the initiation and use of a Secure Channel. These keys are all double length DES keys and are the<br>
following:<br>
• The Secure Channel encryption key (S-ENC) and the Secure Channel MAC key (S-MAC). These keys are only used to generate Secure Channel session keys during the initiation of a Secure Channel.<br>
• The data encryption key (DEK) for decrypting sensitive data, e.g. secret or private keys (Keys updated by PUT KEY command). This key is a  double length DES key and is used as a static key for SCP01, used as a session key for SCP02.</p>
<ul>
<li>Attack on SCP02
<ul>
<li>Plaintext Recovery [<a href="https://pdfs.semanticscholar.org/2ee2/ebe1a1cf2536eb487e9be0a976cb55f41199.pdf">https://pdfs.semanticscholar.org/2ee2/ebe1a1cf2536eb487e9be0a976cb55f41199.pdf</a>]</li>
<li>Sample code<br>
<a href="https://github.com/banh-gao/CNSReader/blob/master/ocf/de/cardcontact/opencard/security/GPSCP02SecureChannel.java">https://github.com/banh-gao/CNSReader/blob/master/ocf/de/cardcontact/opencard/security/GPSCP02SecureChannel.java</a></li>
</ul>
</li>
</ul>
<h3 id="global-platform-specifications-you-have-a0000001510000-to-select-the-card-manager-isd-aid">Global Platform specifications you have <code>A0000001510000</code> to select the card manager (ISD AID)</h3>
<p><strong>SELECT ISD using zero length AID</strong><br>
00 a4 04 00 00<br>
response hex    :<br>
6f 65 84 08 a0 00 00 00 18 43 4d 00 a5 59 73 4a<br>
06 07 2a 86 48 86 fc 6b 01 60 0c 06 0a 2a 86 48<br>
86 fc 6b 02 02 01 01 63 09 06 07 2a 86 48 86 fc<br>
6b 03 64 0b 06 09 2a 86 48 86 fc 6b 04 01 05 65<br>
0b 06 09 2b 85 10 86 48 64 02 01 03 66 0c 06 0a<br>
2b 06 01 04 01 2a 02 6e 01 02 9f 6e 06 19 81 33<br>
10 01 07 9f 65 01 ff<br>
response SW1SW2 : 90 00 (Success)<br>
response ascii  : oe…CM…YsJ…<em>.H…k.`…</em>.H…k…c…<em>.H…k.d…</em>.H…k…e…+…Hd…f…+…*.n…n…3…e…<br>
response parsed :</p>
<p>6f 65 – File Control Information (FCI) Template<br>
84 08 – Dedicated File (DF) Name<br>
a0 00 00 00 18 43 4d 00 (BINARY)<br>
a5 59 – File Control Information (FCI) Proprietary Template<br>
73 4a – Directory Discretionary Template<br>
06 07 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 01 (BINARY)<br>
60 0c – [UNKNOWN TAG]<br>
06 0a – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 02 02 01 01 (BINARY)<br>
63 09 – [UNKNOWN TAG]<br>
06 07 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 03 (BINARY)<br>
64 0b – [UNKNOWN TAG]<br>
06 09 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 04 01 05 (BINARY)<br>
65 0b – [UNKNOWN TAG]<br>
06 09 – Object Identifier (OID)<br>
2b 85 10 86 48 64 02 01 03 (BINARY)<br>
66 0c – [UNKNOWN TAG]<br>
06 0a – Object Identifier (OID)<br>
2b 06 01 04 01 2a 02 6e 01 02 (BINARY)<br>
9f 6e 06 – Visa Low-Value Payment (VLP) Issuer Authorisation Code<br>
19 81 33 10 01 07 (BINARY)<br>
9f 65 01 – [UNKNOWN TAG]<br>
ff (BINARY)<br>
Captured by <a href="https://code.google.com/archive/p/javaemvreader/">https://code.google.com/archive/p/javaemvreader/</a></p>
<h3 id="cplc">CPLC</h3>
<p><strong>Select Global Platform Security Domain</strong><br>
00 a4 04 00 07 <strong>a0 00 00 00 18 43 4d 00</strong><br>
response hex    :<br>
6f 65 84 08 a0 00 00 00 18 43 4d 00 a5 59 73 4a<br>
06 07 2a 86 48 86 fc 6b 01 60 0c 06 0a 2a 86 48<br>
86 fc 6b 02 02 01 01 63 09 06 07 2a 86 48 86 fc<br>
6b 03 64 0b 06 09 2a 86 48 86 fc 6b 04 01 05 65<br>
0b 06 09 2b 85 10 86 48 64 02 01 03 66 0c 06 0a<br>
2b 06 01 04 01 2a 02 6e 01 02 9f 6e 06 19 81 33<br>
10 01 07 9f 65 01 ff<br>
response SW1SW2 : 90 00 (Success)<br>
response ascii  : oe…CM…YsJ…<em>.H…k.`…</em>.H…k…c…<em>.H…k.d…</em>.H…k…e…+…Hd…f…+…*.n…n…3…e…<br>
response parsed :</p>
<p>6f 65 – File Control Information (FCI) Template<br>
84 08 – Dedicated File (DF) Name<br>
<strong>a0 00 00 00 18 43 4d 00</strong> (BINARY- AID also)<br>
a5 59 – File Control Information (FCI) Proprietary Template<br>
73 4a – Directory Discretionary Template<br>
06 07 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 01 (BINARY)<br>
60 0c – [UNKNOWN TAG]<br>
06 0a – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 02 02 01 01 (BINARY)<br>
63 09 – [UNKNOWN TAG]<br>
06 07 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 03 (BINARY)<br>
64 0b – [UNKNOWN TAG]<br>
06 09 – Object Identifier (OID)<br>
2a 86 48 86 fc 6b 04 01 05 (BINARY)<br>
65 0b – [UNKNOWN TAG]<br>
06 09 – Object Identifier (OID)<br>
2b 85 10 86 48 64 02 01 03 (BINARY)<br>
66 0c – [UNKNOWN TAG]<br>
06 0a – Object Identifier (OID)<br>
2b 06 01 04 01 2a 02 6e 01 02 (BINARY)<br>
9f 6e 06 – Visa Low-Value Payment (VLP) Issuer Authorisation Code<br>
19 81 33 10 01 07 (BINARY)<br>
9f 65 01 – [UNKNOWN TAG]<br>
ff (BINARY)<br>
Security Domain FCI<br>
AID: a0 00 00 00 18 43 4d 00 (Gemplus Security Domain)<br>
RID: a0 00 00 00 18 (GEMPLUS [France])<br>
PIX: 43 4d 00<br>
Max Length in Command Data Field      : 255 bytes<br>
Application Prod. Life-Cycle Data     : 198133100107<br>
Tag Allocation Authority (OID)        : globalPlatform 01<br>
Card Management Type and Version (OID): globalPlatform 02020101<br>
Card Identification Scheme (OID)      : globalPlatform 03<br>
Global Platform Version               : 2.1.1<br>
Secure Channel Version                : SCP01 (options: 0x05)<br>
Card Config Details                   : 06092b8510864864020103<br>
Card/Chip Details                     : 060a2b060104012a026e0102</p>
<p><strong>Get Data CPLC (Card Production Life Cycle Data) History File Identifiers</strong><br>
00 ca 9f 7f 00<br>
response hex    :<br>
47 90 6a 15 19 81 33 10 01 07 51 87 00 00 41 62<br>
07 bc 12 92 71 13 50 03 71 13 50 05 71 13 00 00<br>
00 36 00 00 00 00 00 00 00 00<br>
response SW1SW2 : 90 00 (Success)<br>
response ascii  : G.j…3…Q…Ab…q.P.q.P.q…6…<br>
Card Production Life Cycle Data (CPLC)<br>
IC Fabricator: 4790 (NXP)<br>
IC Type: 6a15<br>
Operating System Provider Identifier: 1981<br>
Operating System Release Date: 3310<br>
Operating System Release Level: 0107<br>
IC Fabrication Date: 5187<br>
IC Serial Number: 00004162<br>
IC Batch Identifier: 07bc<br>
IC ModuleFabricator: 1292<br>
IC ModulePackaging Date: 7113<br>
ICC Manufacturer: 5003<br>
IC Embedding Date: 7113<br>
Prepersonalizer Identifier: 5005<br>
Prepersonalization Date: 7113<br>
Prepersonalization Equipment: 00000036<br>
Personalizer Identifier: 0000<br>
Personalization Date: 0000<br>
Personalization Equipment: 00000000<br>
-&gt; Card Unique Identifier: 47906a1507bc00004162</p>
<p>Parser:<br>
<a href="https://www.javacardos.com/tools/apdu-parser.html">https://www.javacardos.com/tools/apdu-parser.html</a></p>
<h2 id="commands-summary">Commands Summary</h2>
<h3 id="management-command">Management Command</h3>
<p>DELETE Command: E4<br>
GET DATA Command: CA or CB<br>
GET STATUS Command: F2<br>
INSTALL Command: E6<br>
LOAD Command: E8<br>
MANAGE CHANNEL Command: 70<br>
PUT KEY Command: D8<br>
SELECT Command: A4<br>
SET STATUS Command: F0<br>
STORE DATA Command: E2<br>
Get Response: 00 C0 00 00 12</p>
<p>Get Status: 84F210020A 4F08 A000000151444143<br>
Select AID: 00A4 0400 0B A000000151000000000000<br>
Store Data:<br>
84E288000D 00CF 0A 11111111111111111111<br>
Get Date:84CA 00CF 00<br>
Response: CF 0A 11111111111111111111 9000<br>
PUT Key:<br>
84 D8<br>
00 (If want to replace previous keyset, this should be set as the version number )<br>
81 4B<br>
20 (Version Number, if it is new keyset, need to increase from previous keyset )<br>
80 10 33D5A2C109787A84124EFC2E06492B1D (Encrypted by DEK session key)<br>
03 5DC50E (KCV: Key checksum value)<br>
80 10 33D5A2C109787A84124EFC2E06492B1D<br>
03 5DC50E<br>
80 10 6D0364647BBADBD5117A15804EA49675<br>
03 5DC50E<br>
E437C28600DB4221</p>
<h3 id="scp">SCP</h3>
<p>INITIALIZE UPDATE Command: 50<br>
EXTERNAL AUTHENTICATE Command: 82</p>
<h3 id="error-codes">Error Codes</h3>
<p>General Error:<br>
‘6400’ No specific diagnosis<br>
‘6700’ Wrong length in Lc<br>
‘6881’ Logical channel not supported or is not active<br>
‘6982’ Security status not satisfied. Happens when SCP establish has issue, or need higher level of SD authentication<br>
‘6985’ Conditions of use not satisfied. Happens when the AID is used or the package is loaded before. Or the key set is not set yet, operation is not allowed.<br>
‘6A86’ Incorrect P1 P2<br>
‘6D00’ Invalid instruction<br>
‘6E00’ Invalid class<br>
Reponse Error:<br>
‘6581’ Memory failure<br>
‘6A88’ Referenced data not found. Happens when the AID used for install for install command and load command are different, or the package is not able to load.<br>
‘6A82’ Application not found<br>
‘6A80’ Incorrect values in command data. Sometimes in the install parameter, e.g. system specific parameters(EF) are not accepted by SE.<br>
‘6A84’ Not enough memory space</p>
<h3 id="extradition">Extradition</h3>
<p>GP 2.1.1, SSD section (concept) and APDU commands Install [for load], [install] and [extradition].<br>
Example:</p>
<ul>
<li>select ISD</li>
<li>open a secure channel</li>
<li>Install [for install &amp; make selectable] on a pre-loaded SD package/module --&gt; optionally you need to specify in the install parameters that this SD accepts extradition</li>
<li>select SSD</li>
<li>open a secure channel (using the default keys)</li>
<li>personalize (put secure channel keys) (This step is must for the below step, otherwise got 6985 error)</li>
<li>install [for load] an application, specify the SD to be associated–&gt; optionally use install [for extradition] and specify the SD to be associated.</li>
</ul>

