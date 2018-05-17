•	Finding square of a numbers greater than 8 and less that 16
xquery version "1.0-ml";

for $i in 8 to 16
return $i*$i



•	Arrange the given input sequence in ascending order {67,89,45,78,23,45,22,90,1,24}
xquery version "1.0-ml";

for $i in (67,89,45,78,23,45,22,90,1,24)
order by $i ascending
return $i



•	Deleting all the documents whose name starts with ‘book’
xquery version "1.0-ml";
xdmp:document-insert("/bookfirst/journal/studentbook.xml", <student>
<id>1</id>
<name>Hello World </name>
</student>);

xdmp:document-insert("/book/journal/book.xml", <student>
<id>1</id>
<name>Hello World book </name>
</student>)

for $uri in cts:uri-match("/book*.xml")
return xdmp:document-delete($uri)





•	Form Fibonacci series using FLOWR expressions

xquery version "1.0-ml";

let $seq := (1 to 10)
for $n in $seq
return if ($n=0)
then 0
else if ($n =1)
then 1
else (($n - 1) + ($n - 2))




•	Loading a document to ML (load documents from your D: drive)
xdmp:document-load("D:/student.xml",
    <options xmlns="xdmp:document-load">
      <uri>/D:/student.xml</uri>
      <repair>none</repair>
      <permissions>{xdmp:default-permissions()}</permissions>
      <metadata>{
        map:map() => map:with("h", "hello")
                  => map:with("w", "world")
      }</metadata>
    </options>)







•	Inserting documents to ML (through query console)
xquery version "1.0-ml";
xdmp:document-insert("books.xml",
  <books xmlns="http://www.marklogic.com/ns/gs-books">
    <book bookid="1">
      <title>A Quick Path to an Application</title>
      <author>
        <last>Smith</last>
        <first>Jim</first>
      </author>
      <publisher>Scribblers Press</publisher>
      <isbn>1494-3930392-3</isbn>
      <abstract>
          This book describes in detail the power of how 
          to use XQuery to build powerful web applications 
          that are built on the MarkLogic Server platform.
      </abstract>
    </book>
  </books>
)



