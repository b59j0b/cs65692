java c
Homework: Web Crawling 
1. Objective In this   assignment, you will work with a   simple   web   crawler   to   measure   aspects   of a   crawl,   study the   characteristics   of the   crawl,   download   web   pages   from   the   crawl   and   gather   webpage   metadata,   all   from pre-selected news websites.
2. Preliminaries To begin we will make use of   an existing open source Java web crawler called crawler4j. This crawler   is   built   upon   the   open   source   crawler4j   library   which   is   located   on   github.   For   complete   details   on   downloading and compiling   see
htps:/githmub.com/yasserg/rzwler4j 
Also   see the document “Instructions for Installing Eclipse and   Crawler4j”   located   on the Assignments   webpage for help.
Note:    You can use any IDE of   your choice. But we have provided   installation instructions   for   Eclipse   IDE   only
3. Crawling Your task is to configure and compile the crawler and then have it crawl a news website. In the interest   of distributing the   load   evenly   and not   overloading   the news   servers,   we have pre-assigned   the   news   sites to be crawled according to your USC ID number, given   in   the table below.The   maximum   pages   to   fetch   can   be   set   in   crawler4j   and   it   should   be   set   to 20,000 to   ensure   a   reasonable   execution   time for this   exercise.   Also,   maximum   depth   should be   set   to 16 to   ensure   that   we limit the crawling.
You should crawl only the news websites assigned to you, and your crawler should be configured so that it does not visit pages outside of the given news website! 


USC ID ends with 


News Sites to Crawl 

Ne wsS ite Na         me 



Root URL 
01~20 
NY Times 

nytimes 

https://www.nytimes.com 
21~40 
Wall Street Journal 

wsj 

https://www.wsj.com 
41~60 
Fox News 

foxnews 

https://www.foxnews.com 
61~80 
USA Today 

usatoday 

https://www.usatoday.com 
81~00 
Los Angeles Times 

latimes 

https://www.latimes.com 
Limit your crawlerso it only visits HTML, doc, pdfand different image format URLs and record the meta. data for those file types
4. Collecting Statistics 
Your primary task is to enhance the crawler so   it   collects   information   about:
1. the    URLs it attempts to fetch,   a   two   column   spreadsheet,   column    1   containing   the   URL   and   column 2 containing the HTTP/HTTPS status code received; name   the file fetch_NewsSite.csv (where the name “NewsSite” is replaced by the news website name in the table above that you   are crawling).   The number of   rows   should be no more than   20,000   as   that   is   our   pre-set   limit.   Column names for this file   can be URL   and   Status
2. the files it successfully downloads,   a   four   column   spreadsheet,   column    1   containing   the URLs   successfully   downloaded,   column   2   containing   the   size   of the   downloaded   file   (in   Bytes, or you can choose your own   preferred unit (bytes,kb,mb)), column   3   containing the   #   of outlinks   found,   and   column   4   containing   the   resulting   content-type;   name   the   file visit_NewsSite.csv;   clearly   the   number   of rows   will   be   less   than   the   number   of rows   in   fetch_NewsSite.csv
3. all of the    URLs (including repeats) that were discovered and   processed   in   some   way;   a   two   column    spreadsheet    where    column    1    contains    the    encountered    URL    and    column    two    an indicator of whether the URL a. resides in the website (OK), orb. points outside of   the website   (N_OK). (A file points out of   the website if   its URL does not start with the initial host/domain   name,    e.g.    when      crawling      USA      Today      news      website      all      inside      URLs      must      start      with www.usatoday.com.)   Name   the   file urls_NewsSite.csv.   This   file   will   be   much   larger   than   fetch_*.csv and visit_*.csv. For   example   for New   York   Times-   the   URL http://www.nytimes.com/section/sports and   the   URL http:/haytimes.com/section/sports are   both   considered   as   residing   in   the   same   website   whereas          the          following          URL          is 代 写Homework: Web CrawlingJava
代做程序编程语言not considered          to          be          in          the          same          website, http://store.nytimes.com/ 
Note1: you   should modify the   crawler   so   it   outputs   the   above   data   into three   separate   csv   files;   you will use them for processing   later;
Note2: all   uses   of   NewsSite   above   should   be   replaced   by   the   name   given   in   the   column   labeled NewsSite Name in the table on page   1.
Note 3: You should denote the units in size column   of   visit.csv.   The best way   would be to   write   the units that you are using in column header name and let the rest of   the   size   data be   in numbers for easier statistical analysis. The hard requirement is   only to   show the units   clearly   and   correctly. 
Based   on   the   information   recorded   by   the   crawler   in   the   output   files   above,   you   are   to   collate   the   following   statistics for a crawl of   your designated news   website:
●    Fetch   statistics:
o      # fetches   attempted:
The total number of   URLs that the crawler attempted to   fetch.   This is usually   equal   to the MAXPAGES   setting   if   the   crawler   reached   that   limit; less   if   the   website   is   smaller   than   that.
o      # fetches   succeeded:
The number of   URLs that were successfully downloaded in their   entirety,   i.e. returning   a   HTTP   status code of   2XX.
o    #   fetches   failed   or   aborted:
The number of   fetches that failed for whatever reason, including,   but not   limited   to:   HTTP redirections   (3XX),   client errors (4XX),   server errors (5XX)   and   other network-related   errors.   1
●    Outgoing URLs: statistics about URLs extracted   from visited   HTML   pages
o         Total URLs extracted:
The grand total number of   URLs extracted (including repeats)   from   all   visited   pages
o         # unique URLs extracted:
The   number   of unique URLs   encountered   by   the   crawler
o         # unique URLs within your news website:
The number of unique URLs encountered that are associated with   the news   website,
i.e. the   URL   begins   with   the   given   root   URL   of   the   news   website, but   the   remainder   of   the URL is   distinct
o         # unique URLs outside the news website:
The   number   of unique URLs   encountered   that   were not from   the   news   website.
●    Status   codes:   number   of times   various   HTTP   status   codes   were   encountered   during   crawling,   including   (but   not   limited   to): 200, 301, 401, 402,   404,etc.
●    File sizes:   statistics about file sizes   of   visited   URLs - the number   of   files   in   each   size   range   (See Appendix A).
o          1KB =   1024B;   1MB   =   1024KB
●   Content Type: a list of   the   different   content-types   encounteredThese statistics should be collated and submitted as a plain text file whose name is   CrawlReport_NewsSite.txt, following the format given in Appendix A at   the end of   this document.   Make   sure you understand the   crawler   code   and required   output before   you   commence   collating   these statistics.For efficient crawling it is a good idea to   have multiple   crawling   threads. You are required to use multiple threads in this exercise. crawler4j   supports   multi-threading   and   our   examples   show   setting   the   number   of crawlers   to   seven   (see   the   line   in   the   code   int   numberOfCrawlers   =   7;).   However,   if you   do   a   naive   implementation   the   threads   will   trample   on   each   other   when   outputting   to your   statistics   collection   files.   Therefore you need to   be   a bit   smarter   about   how   to   collect the statistics, and crawler4j documentation has a   good   example   of   how to   do this.   See both   of   the following links   for   details:
-examples/crawler4-examples- 
base/src/testjava/edu/ucifics/orawler4jexamples/multiple/Multiplecrawlercomtroller,java 
and
https://github.com/yasserg/crawler4j/blob/master/crawler4j-examples/crawler4j-examples- base/src/test/java/edu/uci/ics/crawler4j/examples/localdata/LocalDataCollectorCrawler.java 
All the information that you are required to collect can be derived by processing the crawler output. 



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
