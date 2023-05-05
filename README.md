Download Link: https://assignmentchef.com/product/solved-cx4031-project-2-understanding-a-friendly-query-optimizer
<br>
A DBMS query optimizer executes a query execution plan (QEP) to process a query. As a database administrator, you would like to understand and visualize the performance of the query optimizer for processing queries. This is a typical task an administrator may perform in an organization to comprehend why certain queries or applications are slow. Fortunately, you do not have to write a software to do it. There is a tool called PICASSO <a href="http://dsl.cds.iisc.ac.in/projects/PICASSO/">(</a><a href="http://dsl.cds.iisc.ac.in/projects/PICASSO/">http://dsl.cds.iisc.ac.in/projects/PICASSO/</a><a href="http://dsl.cds.iisc.ac.in/projects/PICASSO/">)</a> that can aid you to understand and visualize the performance of a query optimizer.




<h1>PROJECT DESCRIPTION</h1>

Download the PICASSO tool and install it on your database. Guideline for installing it detailed in the <em>Appendix</em>. Note that you may need to update the JDBC driver to make it work. Specifically, you will use the PICASSO tool to achieve the following two key goals of the project:

<ul>

 <li><strong>Generate and describe the plan, cost, and cardinality diagrams for a set of queries</strong>. You should use the TPC-H benchmark data and queries described below. You are encouraged to read the software documentation of PICASSO</li>

</ul>

<a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Picasso2Doc.pdf">(</a><a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Picasso2Doc.pdf">https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Picasso2Doc </a><a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Picasso2Doc.pdf">.pdf</a><a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Picasso2Doc.pdf">)</a> as well related information in the PICASSO website to get familiarize with the concepts related to plan, cost, and cardinality estimation diagrams.




<ul>

 <li><strong>Design and implement an algorithm</strong> that takes as input a query, retrieves its query execution plan, and returns as output an <strong>explanation</strong> (i.e., reason) that describes the reason why the underlying RDBMS selected this plan among many others. You should exploit the PICASSO tool to generate the explanation. Note that the structure of explanation is open-ended. It can be in the form of natural language or in a more structured form. You are encouraged to develop a visual interface that facilitates user-friendly interaction with your software.</li>

</ul>

Your goal is to ensure generality of the solution (i.e., it can handle a wide variety of queries) and the explanation should be <strong>precise and accurate</strong>. <em>Hint: You need to transform the input query to a PICASSO query template in order to generate explanation. Check the guideline in the Appendix to see which part of the PICASSO code you need to understand.</em>




You should use <strong>Python or Java</strong> as the host language on <strong>Windows</strong> platform for your project. The DBMS allowed in this project is <strong>PostgreSQL. </strong>The dataset and queries you should use for this project is<strong> TPC-H </strong>(see <em>Appendix</em>). You are free to use any off-theshelf toolkits for your project.




For students using <strong>Mac</strong> platform, you can <strong>install Windows on your Mac</strong> by following instructions in <a href="https://support.apple.com/en-sg/HT201468">https://support.apple.com/en-sg/HT201468</a><a href="https://support.apple.com/en-sg/HT201468">.</a>




Note that several parts of the project are left open-ended (e.g., what will be the content of the explanation? how the GUI should look like? What are the functionalities we should support?) deliberately so that the project does not curb a group’s creative endeavors. You are free to make realistic assumptions to achieve these tasks.

<strong> </strong>

<table width="628">

 <tbody>

  <tr>

   <td width="50"><strong>I.</strong></td>

   <td width="578"><strong><u>Creating TPC-H database in PostgreSQL</u></strong></td>

  </tr>

 </tbody>

</table>

Follow the following steps to generate the TPC-H data:

<ul>

 <li>Go to <a href="http://www.tpc.org/tpc_documents_current_versions/current_specifications5.asp">http://www.tpc.org/tpc_documents_current_versions/current_specifications5.asp</a> and download TPC-H Tools v2.18.0.zip. Note that the version may defer as the tool may have been updated by the developer.</li>

 <li>Unzip the package. You will find a folder “dbgen” in it.</li>

 <li>To generate an instance of the TPC-H database:

  <ul>

   <li>Open up tpch.vcproj using visual studio software.</li>

   <li>Build the tpch project. When the build is successful, a command prompt will appear with “TPC-H Population Generator &lt;Version 2.17.3&gt;” and several *.tbl files will be generated. You should expect the following .tbl files: customer.tbl, lineitem.tbl, nation.tbl, orders.tbl, part.tbl, partsupp.tbl, region.tbl, supplier.tbl</li>

   <li>Save these .tbl files as .csv files</li>

   <li>These .csv files contain an extra “|” character at the end of each line. These “|” characters are incompatible with the format that PostgreSQL is expecting. Write a small piece of code to remove the last “|” character in each line. Now you are ready to load the .csv files into PostgreSQL Open up PostgreSQL. Add a new database “TPC-H”.</li>

   <li>Create new tables for “customer”, “lineitem”, “nation”, “orders”, “part”,</li>

  </ul></li>

</ul>

“partsupp”, “region” and “supplier”

<ul>

 <li>Import the relevant .csv into each table. Note that pgAdmin4 for PostgreSQL (windows version) allows you to perform import easily. You can select to view the first 100 rows to check if the import has been done correctly. If encountered error (e.g., ERROR: extra data after last expected column) while importing, create columns of each table first before importing. Note that the types of each column has to be set appropriately. You may use the SQL commands in Appendix II to create the tables.</li>

</ul>




<strong>             </strong>

<table width="628">

 <tbody>

  <tr>

   <td width="50"><strong>II.</strong></td>

   <td width="578"><strong><u>SQL commands for creating TPC-H data tables</u></strong></td>

  </tr>

 </tbody>

</table>




Region table




<ul>

 <li>Nation table</li>

</ul>







<ul>

 <li>Part table</li>

</ul>







<ul>

 <li>Supplier table</li>

</ul>







<ul>

 <li>Partsupp table</li>

</ul>




<ul>

 <li>Customer table</li>

</ul>




<ul>

 <li>Orders table</li>

</ul>







<ul>

 <li>Lineitem table</li>

</ul>







<table width="628">

 <tbody>

  <tr>

   <td width="50"><strong>III.</strong></td>

   <td width="578"><strong><u>Installing and Using PICASSO</u></strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<ul>

 <li>Download picasso2.1.zip from https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/license.htm</li>

</ul>

Follow installation instruction in:

<a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Installation/installation.htm">https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Installation/installati </a><a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Installation/installation.htm">on.htm</a> <strong><u>Note:</u></strong><strong>  </strong>

<strong>Install Java 3D 1.5.1 (https://www.oracle.com/java/technologies/java-archivedownloads-java-client-downloads.html#java3d-1.5.1-oth-JPR). </strong>

<strong>Upon installation, copy the three .jar (j3dcore.jar, j3dutils.jar and vecmath.jar) and j3dcore-ogl.dll (for Windows) to ..picasso2.1picasso2.1Libraries.  </strong>




<ul>

 <li>Guide on how to use the PICASSO GUI is found here: <a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Usage/controls.htm">https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Usage/controls.h </a><a href="https://dsl.cds.iisc.ac.in/projects/PICASSO/picasso_download/doc/Usage/controls.htm">tm</a></li>

</ul>




<strong><u>Note: For Part (b) of the project, you would need to explore the code of PICASSO. A</u></strong><strong> <u>good place to start is PicassoDiagram.java inside the PicassoServer folder. The .java</u> <u>provides the logic of generating the diagrams used in PICASSO GUI.</u> </strong>

<strong> </strong>