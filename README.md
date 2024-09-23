[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/J7-Ztghw)


# CS6200 / IS4200: Relevance Judgments: Muhammad Hamza Mubashir NUID 002370588

# Problem Statement

TLDR: In this assignment, you will choose three topics represented in the _Chronicling America_ collection of historic newspapers and record the text of passages relevant to those topics in the file `topics.xml`.

As we discussed in class, the most common way to evaluate ad hoc information retrieval systems is to create *test collections*, as in the [Text Retrieval Conferences (TREC)](https://trec.nist.gov/) run by the US [National Institute of Standards and Technology](https://www.nist.gov/). These consist of a set of information needs, called *topics*. Each topic contains a brief query (the **title**) and longer natural language query (the **description**) and an even longer **narrative** that explains what the user was looking for an what kinds of information count as relevant or not for that information need.

Here is one example TREC topic:

| field | contents |
| ----- | -------- |
| title | pet therapy |
| description | How are pets or animals used in therapy for humans and what are the benefits? |
| narrative | Relevant documents must include details of how pet- or animal-assisted therapy is or has been used. Relevant details include information about pet therapy programs, desscriptions of the circumstances in which pet therapy is used, the benefits of this type of therapy, the degree of success of this therapy, and any laws or regulations governing it. |

After these topics are created, annotators feed the queries to search engines and create *relevance judgments* by looking through the results. The document identifiers of relevant and non-relevant results are appended to each topic.

In this assignment, you will go through the process of creating relevance judgments for an existing set of topics created by the Library of Congress for their [_Chronicling America_](https://chroniclingamerica.loc.gov/) project, which digitized millions of pages of historic newspapers. As part of this project, librarians have created &ldquo;Research Guides&rdquo; on a few hundred topics. Here is [an alphabetical list of these research guides](https://guides.loc.gov/chronicling-america-topics/alphabetical-order), which you can also view by date, library subject heading, and some other categories.

As an example, consider the research guide for the [bicycle craze in the years around 1900](https://guides.loc.gov/chronicling-america-bicycle-craze). In addition to the narrative and a timeline of events, you can click [&ldquo;Read more about it!&rdquo;](https://guides.loc.gov/chronicling-america-bicycle-craze/selected-articles) to see a list of suggested queries and a few example relevant documents. For most topics, these relevant documents are by no means exhaustive.

**Your task** is to choose **three research guides** and judge the relevance of search results to those topics.  This is made more complex than some evaluations because this is a **passage retrieval** task, i.e., only some of the text on each newspaper page may be relevant to the topic. For instance, [here is the first page listed for the Bicycle Craze topic](https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/#words=bicycles+safety).  Only some of the second column is relevant. Your job, therefore, is to judge whether pages are relevant and, if so, what text on that page is relevant.

You should select relevant passages for all of the documents list on your topics' &ldquo;Read more about it!&rdquo; page. In addition, you should judge **ten additional** documents by constructing a query and searching *Chronicling America*.  For these ten, some of the results may be judged relevant and some non-relevant.  You will record your judgements in a simple XML file.  We have provided the skeleton structure in `topics.xml` for you to edit.  In `bicycle-example.xml`, we show what information you should record:
```xml
<topics>
  <topic>
    <id>https://guides.loc.gov/chronicling-america-bicycle-craze</id>
    <results>
      <result>
	<id>https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/</id>
	<rel>1</rel>
	<text>THE WORLD ON WHEELS
The Improvements Made The
...
      </text>
      </result>
      <result>
	<id>https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-03-17/ed-1/seq-11/</id>
	<rel>1</rel>
	<text>ASTRIDE THE WHEEL
Another Plea in Behalf of the
...
      </text>
    </result>
    <result>
      <id>https://chroniclingamerica.loc.gov/lccn/sn88085722/1891-07-01/ed-1/seq-2/</id>
      <rel>0</rel>
    </result>
  </results>
</topic>
</topics>
```

Each `<topic>` tag should contain an `<id>`, with the URL of the Research Guide, and a `<results>` tag with one or more `<result>` tags.  Each `<result>` contains:
* an `<id>` tag with the URL of the newspaper page,
* a `<rel>` tag containing 1 for relevant or 0 for non-relevant, and
* a `<text>` tag, if the document is relevant, containing the text of the relevant passage.

In recording page URLs, please remove the information after `#words=` used to highlight search terms.  To find the text of a newspaper page, click on the Text link just above the image.  For example, [here is the text of the first result for the Bicycle Craze topic](https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/ocr/).  (Note that you could also construct this link by appending `/ocr` to the main URL for the newspaper page.) Select the text of the relevant passage and copy it into the `<text>` tag for the result.

Once you have added all this information for three topics to the `topics.xml` file, check in your changes and push them to GitHub.

# Answer Formulation and Methodology
## Part 1 - Topics from Chronicling America - Requirement Breakdown
1. Find 3 Topics from the Chronicling America Project.
2. For these 3 Topics from the "Read More About it" section find the list of suggested relevant documents.
3. From these suggested documents judge if they are relevant or not and if relevant mention the relevant text in the passages under the <text></text> headers Do this for all the suggested documents / newspaper pages that are returned for that topic.

## Part 2 - Additional Documents on those Topics - Requirement Breakdown
1. In addition for each of the 3 Topics find 10 additional documents for each of the topics and add it to the topics.xml.


## Selected Topics for Part 1
1. [Race to the North Pole](https://guides.loc.gov/chronicling-america-race-north-pole)
2. [Building the Titanic](https://guides.loc.gov/chronicling-america-building-titanic)
3. [Theft of Mona Lisa](https://guides.loc.gov/chronicling-america-theft-mona-lisa)


## Additional Documents for Part 2

10 additional documents were found for each of the above topics and were also judged for relevance and added to the topics.xml as part of the requriement for the assignment.

## Selected Articles for Topic 1 "Race to the North Pole"
1. "Nations Pay Tribute to Cook" **(Relevant Text Extracted)**
    - The San Francisco Call (San Francisco, CA), September 3, 1909, Page 1, Image 1, col. 5-7.
2. "Peary Tells World He Has Found North Pole; No Trace to Show That Dr. Cook Preceded Him" **(Error on Loading Newspaper Image: Unable to open [object Object]:HTTP 0 attempting to load Tile Source)**
    - The Times Dispatch (Richmond, VA), September 7, 1909, Image 1, col. 1, 6-7.
3. "Question of Priority in the Discovery of the North Pole"
    - The Ogden Standard (Ogden City, UT), September 7, 1909, Image 1, col. 1-2.
4. "Feud of Explorers Arouses Scientists" **(Relevant Text Extracted)**
    - The Washington Times (Washington, D.C.), September 8, 1909, Last Edition, Page 3, Image 3, col. 1.
5. "Peary Also Reached the North Pole" **(Relevant Text Extracted)**
    - The Farmville Herald (Farmville, VA), September 10, 1909, Page 2, Image 2, col. 1-2.
6. "Cook-Peary Dispute" **(Relevant Text Extracted)**
    - New-York Tribune (New York, NY), September 12, 1909, Page 2, Image 2, col. 3.
7. "Tuesday Will See Both Explorers From Arctic Circle in America and Some Facts Will Be Made Plain" **(Relevant Text Extracted)**
    - The Paducah Evening Sun (Paducah, KY), September 18, 1909, Image 1, col. 5.
8. "Says Peary and Cook Both Reached Pole" **(Relevant Text Extracted)**
    - Gainesville Daily Sun (Gainesville, FL), September 30, 1909, Image 9, col. 1-2.
9. "State Department is Not Ready to Take its Stand" **(Relevant Text Extracted)**
    - The Salt Lake Herald-Republican (Salt Lake City, UT), November 5, 1909, Image 1, col. 6-7. 

## Selected Articles as 10 Additional Documents for Topic 1 filtered from 1909 - 1911
1. Coeur d'Alene evening press. (Coeur d'Alene, Idaho), September 29, 1909, Page 2, Image 2 **(Relevant Text Extracted)**
2. The times and democrat. [volume] (Orangeburg, S.C.), September 11, 1909, Page 2, Image 2 **(Relevant Text Extracted)**
3. Kentucky Irish American. (Louisville, Ky.), January 08, 1910, Image 3 **(Not Relevant)**
4. Connecticut western news. [volume] (Salisbury, Litchfield Co., Conn.), February 10, 1910, Page 2, Image 2 **(Not Relevant)**
5. The gazette. [volume] (Cleveland, Ohio), April 02, 1910, Page 3, Image 3 **(Not Relevant)**
6. Decorah public opinion. (Decorah, Winneshiek County [Iowa]), September 22, 1909, Image 1 **(Relevant Text Extracted)**
7. The Pensacola journal. (Pensacola, Fla.), August 29, 1909, Section 1, Page 5, Image 5 **(Not Relevant)** 
8. The Barre daily times. (Barre, Vt.), September 22, 1909, Page 4, Image 4 **(Not Relevant)**
9. Norwich bulletin. [volume] (Norwich, Conn.), October 04, 1909, Page 4, Image 4 **(Relevant Text Extracted)**
10. The Birmingham age-herald. [volume] (Birmingham, Ala.), July 10, 1909, Page 4, Image 4 **(Not Relevant)**

## Selected Articles for Topic 2 "Building the Titanic"
1. "White Star Line to Build Biggest Ships Yet Projected" **(Relevant Text Extracted)**
    - Los Angeles Herald (Los Angeles, CA), April 23, 1908, Page 1, Image 1, col. 6.
2. "Mammoth Liners Puzzle Officials" **(Relevant Text Extracted)**
    - The Washington Times (Washington, DC), October 2, 1908, Last Edition, Page 9, Image 9, col. 4.
3. "One Million for a Starter" **(Relevant Text Extracted)**
    - New-York Tribune (New York, NY), January 3, 1909, Page 7, Image 59, col. 6.
4. "Two New Giants of Sea" **(Relevant Text Extracted)**
    - New-York Tribune (New York, NY), May 30, 1909, Page 8, Image 59, col. 3.
5. "The World’s Largest Vessel, the Titanic, Now Being Built" **(Relevant Text Extracted)**
    - The Daytona Daily News (Daytona, FL), January 8, 1910, Page 1, Image 1, col. 3.
6. "Ships to be the Largest" **(Relevant Text Extracted)**
    - The Washington Herald (Washington, DC), January 23, 1910, Second Part, Page 1, Image 14, col. 2.
7. "Monster Liners" **(Relevant Text Extracted)**
    - Deseret Evening News (Great Salt Lake City, UT), February 4, 1910, Page 3, Image 3, col. 2.
8. "Tells of New Liners Soon to be Launched" **(Relevant Text Extracted)**
    - New-York Tribune (New York, NY), July 11, 1910, Page 3, Image 3, col. 1.
9. "Monster Liner Launched" **(Relevant Text Extracted)**
    - Evening Star (Washington, DC), May 31, 1911, Page 5, Image 5, col. 8.
10. "Titanic's Maiden Trip" **(Relevant Text Extracted)**
    - The Calumet News (Calumet, MI), April 3, 1912, Page 1, Image 1, col. 6.
11. "Titanic Sails on Her First Voyage" **(Relevant Text Extracted)**
    - The Richmond Palladium (Richmond, VA), April 10, 1912, Page 1, Image 1, col. 4.

## Selected Articles as 10 Additional Documents for Topic 2 filtered from Start - 1911
1. The Richmond palladium and sun-telegram. [volume] (Richmond, Ind.), October 20, 1910, Page PAGE TWO, Image 2 **(Relevant Text Extracted)**
2. Norwich bulletin. [volume] (Norwich, Conn.), March 08, 1910, Page 2, Image 2 **(Relevant Text Extracted)**
3. The Minneapolis journal. [volume] (Minneapolis, Minn.), May 01, 1901, Page 4, Image 5 **(Not Relevant)**
4. The Salt Lake herald. [volume] (Salt Lake City [Utah]), August 17, 1899, Page 4, Image 4 **(Not Relevant)**
5. Hopkinsville Kentuckian. [volume] (Hopkinsville, Ky.), April 27, 1911, Page 7, Image 7 **(Relevant Text Extracted)**
6. The Spokane press. [volume] (Spokane, Wash.), November 11, 1910, Page 11, Image 11 **(Relevant Text Extracted)**
7. Evening bulletin. [volume] (Honolulu [Oahu, Hawaii]), August 19, 1909, 3:30 EDITION, Page 8, Image 8 **(Relevant Text Extracted)**
8. Daily capital journal. (Salem, Oregon), March 17, 1909, FIRST EDITION, Image 1 **(Not Relevant)**
9. The Chickasha daily express. (Chickasha, Indian Territory [Okla.]), July 21, 1910, Page PAGE TWO, Image 2 **(Relevant Text Extracted)**
10. Omaha daily bee. (Omaha [Neb.]), August 03, 1910, Page 10, Image 10 **(Not Relevant)**

## Selected Articles for Topic 3 "Theft of Mona Lisa"
1. "Rare Canvas Gone" **(Relevant Text Extracted)**
    - The Appeal (Saint Paul, MN), August 20, 1910, Image 1, col. 6.
2. "Disappearance of the "Mona Lisa" Recalls Theft of Famous Gainsborough" **(Relevant Text Extracted)**
    - The Citizen (Honesdale, PA), September 6, 1911, Page 6, Image 6, col. 1.
3. "Leonardo's Lady" **(Relevant Text Extracted)**
    - The University Missourian (Columbia, MO), May 23, 1912, Image 2, col. 3.
4. "Trying to Steal Mona Lisa's Sister" **(Relevant Text Extracted)**
    - El Paso Herald (El Paso, TX), October 26, 1913, Church and Feature Section, Image 30, col. 6.
5. "Stole 'Mona Lisa' to Avenge Italy" **(Relevant Text Extracted)**
    - The Evening Star (Washington, DC), December 13, 1913, Page 4, Image 4, col. 1.
6. "Mona Lisa" Recovered; Thief is in Custody" **(Relevant Text Extracted)**
    - The Salt Lake Tribune (Salt Lake City, UT), December 13, 1913, Page 12, Image 12, col. 3.
7. "How Painting was Found" **(Relevant Text Extracted)**
    - The Omaha Daily Bee (Omaha, NE), December 14, 1913, Part One, Page 4-A, Image 4, col. 1.
8. "Safeguarding the Treasures of the Louvre" **(Relevant Text Extracted)**
    - The Omaha Daily Bee (Omaha, NE), February 15, 1914, Part Two, Image 20, col. 1.
9. "The Restored Mona Lisa" **(Relevant Text Extracted)**
    - The Evening Star (Washington, DC), March 20, 1914, Page 10, Image 10, col. 2.
10. "Mona Lisa" Thief on Trial" **(Relevant Text Extracted)**
    - The Daily Ardmoreite (Ardmore, OK), June 5, 1914, Page 4, Image 4, col. 4.
11. "The Mona Lisa Thief" **(Relevant Text Extracted)**
    - The Evening Star (Washington, DC), June 6, 1914, Page 6, Image 6, col. 1.
12. "Paintings of Celebrated Artists: "Mona Lisa" or "The Quest of a Woman's Soul" Increases in Fame" **(Relevant Text Extracted)**
    - El Paso Herald (El Paso, TX), February 8, 1919, HOME EDITION, Cable News, Sport and Classified Section, Image 20, col. 1.

## Selected Articles as 10 Additional Documents for Topic 3 filtered from Start to 1919
1. The Hattiesburg news. (Hattiesburg, Miss.), December 16, 1913, Image 7 **(Relevant Text Extracted)**
2. The daily Alaskan. [volume] (Skagway, Alaska), August 26, 1914, Image 4 **(Not Relevant)**
3. Evening capital news. (Boise, Idaho), June 05, 1914, Image 1 **(Relevant Text Extracted)**
4. Bismarck daily tribune. [volume], April 01, 1914, Image 8 **(Relevant Text Extracted)**
5. Aberdeen herald. [volume], September 07, 1911, Page THREE, Image 3 **(Relevant Text Extracted)**
6. The evening times. [volume], December 19, 1913, Image 10 **(Relevant Text Extracted)**
7. Las Vegas optic., March 31, 1914, CITY EDITION, Page THREE, Image 3 **(Relevant Text Extracted)**
8. East Oregonian : E.O., December 17, 1913, DAILY EVENING EDITION, Page PAGE THREE, Image 3 **(Relevant Text Extracted)**
9. The daily star-mirror. (Moscow, Idaho), November 08, 1911, Image 3 **(Not Relevant)**
10. The Pensacola journal., January 05, 1912, Page 7, Image 7 **(Relevant Text Extracted)**
