Download Link: https://assignmentchef.com/product/solved-cse-512-assignment-2
<br>
The required task is to build a simplified query processor that accesses data from the partitioned ratings table.

<strong>Required Task: – </strong>Below are the steps you need to follow to fulfill this assignment:




RangeQuery() – o Implement a Python function <em>RangeQuery </em>that takes as input: (1)

<em>RatingMinValue </em>(2) <em>RatingMaxValue </em>(3) <em>openconnection (4) outputPath</em> o Please note that the <em>RangeQuery </em>would not use ratings table but it would use the range and round robin partitions of the ratings table.

<ul>

 <li><em>RangeQuery</em>() then returns all tuples for which the <em>rating </em>value is larger than or equal to <em>RatingMinValue </em>and less than or equal to <em>RatingMaxValue</em>.</li>

 <li>The returned tuples should be stored in outputPath. Each line represents a tuple that has the following format such that <em>PartitionName </em>represents the full name of the partition i.e. <em>RangeRatingsPart1 </em>or <em>RoundRobinRatingsPart4 </em> in which this tuple resides.</li>

</ul>

<strong><em>PartitionName</em>, <em>UserID</em>, <em>MovieID</em>, <em>Rating</em></strong> Example:

<strong><em>RangeRatingsPart0,1,377,0.5</em></strong>

<strong><em>RoundRobinRatingsPart1,1,377,0.5</em></strong>




<ul>

 <li>Note: Please use ‘,’ (COMMA, no space character) as delimiter between <em>PartitionName</em>, <em>UserID</em>, <em>MovieID </em>and <em>Rating</em>.</li>

</ul>




PointQuery() – o Implement a Python function <em>PointQuery </em>that takes as input: (1) <em>RatingValue</em>.

(2) <em>openconnection (3) outputPath</em> o Please note that the <em>PointQuery </em>would not use ratings table but it would use the range and round robin partitions of the ratings table.

<ul>

 <li><em>PointQuery</em>() then returns all tuples for which the <em>rating </em>value is equal to <em>RatingValue</em>.</li>

 <li>The returned tuples should be stored in outputPath. Each line represents a tuple that has the following format such that <em>PartitionName </em>represents the full name of the partition i.e. <em>RangeRatingsPart1 </em>or <em>RoundRobinRatingsPart4 </em> in which this tuple resides.</li>

</ul>

<strong><em>PartitionName</em>, <em>UserID</em>, <em>MovieID</em>, <em>Rating</em></strong>

Example

<strong><em>RangeRatingsPart3,23,459,3.5</em></strong>

<strong><em>RoundRobinRatingsPart4,31,221,0</em></strong>




<ul>

 <li>Note: Please use ‘,’ (COMMA, no space character) as delimiter between <em>PartitionName</em>, <em>UserID</em>, <em>MovieID </em>and <em>Rating</em>.</li>

</ul>




Please use the <strong>function signature exactly same as mentioned in Assignment2_Interface.py </strong>.




<strong>Naming Convention to be followed strictly:</strong>     Database name – <em>ddsassignment2</em>

Name of Rating table – <em>ratings</em>

Postgres User name – <em>postgres</em>     Postgres password – <em>1234</em>




<strong>How to use tester.py:</strong>

Open the Assignment2.zip file and dump all the contents in a folder.

Also move <em>ratings.dat </em>file to this folder.

As per the naming conventions provided above, setup your postgresql.

Once the setup is done, test the tester.py by simply running it.

It should provide the following output:




Now, you can implement your functions in Assignment2_Interface.py and once done, use the tester again to generate the output.

<strong>DONOT CHANGE </strong>tester.py and Assignment1.py. Changing anyone of these would cause problems and the system will stop working, and may lead to <strong>deduction of marks</strong>.

<strong>PLEASE  KEEP  IN MIND</strong>,  this tester is just for your help. For grading  purpose,  an additional set of test cases would be used. It will try to break your code. So, please provide the functionalities accordingly, so that it handles all possible scenarios.







<ol>

 <li>Only submit the .py file. Do <strong>not</strong> change the file name. Do <strong>not</strong> put it into a folder or upload a zip.</li>

 <li>Multiple submissions are allowed. Only the latest submission will be graded. No late submission is accepted.</li>

</ol>







<strong>Note: –</strong> Failure to follow the instructions provided in the document will result in the loss of the points.




<ol>

 <li><em>Ratings</em></li>

</ol>







<ol start="2">

 <li><em>RangeRatingsPart0 </em>to <em>RangeRatingsPartN </em>(where N = number of partition – 1)

  <ol>

   <li>Same structure as <em>Ratings </em>table</li>

   <li>If value of N is 5 then here is the list of table created for Range Partitioning.</li>

  </ol></li>

</ol>







<ol start="3">

 <li><em>RoundRobinRatingsPart0 </em>to <em>RoundRobinRatingsPartN  </em>(where N = number of partition – 1)

  <ol>

   <li>Same structure as <em>Ratings </em>table</li>

   <li>If value of N is 5 then here is the list of table created for Round Robin Partitioning</li>

  </ol></li>

</ol>







<ol start="4">

 <li><em>RangeRatingsMetadata</em></li>

</ol>




If <em>PartitionNum </em>is 0, then it means table <em>RangeRatingsPart0 </em>is being referred and this table contains records for rating values &gt;= minrating and &lt;= maxrating.

If <em>PartitionNum </em>is N ( N &gt; 1), then it means table <em>RangeRatingsPartN </em>is being referred and this table contains records for rating values &gt; minrating and &lt;= maxrating.

Example: – If N is 1, the <em>RangeRatingsPart1 </em>is being referred and this partition contains all the record for which the rating values are 1 &lt; value &lt;= 2.







<ol start="5">

 <li><em>RoundRobinRatingsMetadata</em></li>

</ol>




<em>Partitionnum </em>denotes total number of partition and <em>tablenextinsert </em>denotes that next partition the record should be inserted.