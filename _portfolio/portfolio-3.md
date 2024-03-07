# Attendance at the National Cinematheque of Mexico during 2019 - 2023
![cineteca](/images/image_3.jpg)

<h3> Introduction </h3>

This report presents a data analytics work on attendance preferences at the Cineteca Nacional de México, where it explores by year, director, cycle, country and most viewed films in the years 2019 to March 2023, including attendance data during the COVID-19 pandemic and its impact on this. The goal of this analysis is to identify attendance patterns and trends in audience film selection, as well as to understand how the pandemic has affected attendance habits and film preferences. In addition, it seeks to provide valuable information for decision-making related to film programming and the marketing strategy of the Cineteca Nacional in the current and future context.
<br> </br>
<h3> Methodology </h3>
The data were extracted from the website <a href="https://datos.gob.mx/busca/dataset/titulos-proyectado-con-asistencia"> Datos Abiertos de México</a>, where they were collected through the titles exhibited at the Cineteca Nacional and retrieved through its management system. The data were loaded into a database hosted in Google Cloud's BigQuery, using the test space of this platform and cleaned through different SQL queries.
<br> </br>
<h3> Results </h3>
<h4> Attendance habits </h4>
<h5>Annual</h5>
During 2019 there was an average monthly attendance of 108,792 people, having peaks during the Academy Awards season in the months of January, February and March, and during the summer having the highest attendance in July with 129,163 people. In 2020 the highest peak was in January with 124,339 people, a monthly average of 32,154 people, 70.53% less attendance due to the Covid-19 outbreak and the consequent closing of theaters in Mexico for 4 months and in its reopening, having less attendance due to the pandemic. In 2021, during the Month of January public venues were closed again due to the pandemic and upon reopening in February, had lower attendance with 1,936 people, having a peak with the highest attendance in the summer with 59,313 people in June, growing 26.4% compared to last year, having a monthly average of 40,647 attendees.
During the year 2022, after leaving the pandemic restrictions, monthly attendance rose dramatically with 73.77% more than last year, with an average of 70,659 monthly attendees, giving a peak attendance in December with 122,113 people being this a consequence of the premiere of the movie Pinocchio which we will talk about in the next point. Comparing this year's attendance to the pre-pandemic period, attendance was down 35.05% from 2019.  At the time of analysis, the data set was current through March 2023, having a monthly average of 78,663 monthly attendance and with peak attendance of 82,497 people in the month of March, up 11.33% this quarter.
<h5>Director and film</h5>
The analysis showed that certain directors attract a large part of the public, with Guillermo del Toro and his film Pinocchio obtaining 92,805 attendees during the analysis period, coinciding that it was his work in first place, in second place we have Parasites and Pedro Almodovar with 49,252 attendees and 58,853 attendees respectively. With films such as Dolor y Gloria, Joker, Roma and Clímax, and directors such as Bong Joon-Ho, Martin Scorsese, Alfonso Cuarón and Todd Phillips following in the groups with the highest attendance, with a possible relationship between academy nominations and awards and people's decision to attend a film.
<h5>cycle</h5>
CC Cycles (Classic CNA) correspond to 60.20% of the majority of attendees in the period, with 1,633,981 attendees, premieres are the second majority with 36.37% of attendance, these being 987,246 attendees.
<h5>Country</h5>
For this part of the analysis, two metrics were taken into account, attendance and functions per country of origin of the film, with Mexico being the country with the highest attendance with 655,695 people and 14,881 functions during the period, having an average of 44 attendees per function, but within the five countries with the highest attendance and most functions it is below the average which is 65 attendees per function, with the United States being the country with the highest attendance, 590,190 attendees during the period and 4,977 functions with an average of 118 attendees per function, followed by France with 443,070 attendees and 9,764 functions with an average attendance of 45 people per function, in fourth place we have the United Kingdom with 136,989 attendees and 2,043 functions giving an average of 67 people per function and in fifth place we have Spain with 123,680 attendees and 2,301 functions with its corresponding average of 53 attendees per function.
<br> </br>
<h3> Conclusion </h3>
<ul>
    <li>Attendance at the National CIneteca has been affected by the COVID-19 pandemic with a 70.53% drop in 2020 and despite recovery beginning in 2021, has not yet recovered to pre-pandemic levels.</li>
    <li>Peak attendance seasons are during the Academy Awards season and in the summer.</li>
    <li>Directors such as Guillermo Del Toro and Pedro Almodóvar, as well as the Cineteca Nacional's classic film series and premieres, attract large audiences.</li>
    <li>United States has the largest attendance and Mexico has the most screenings.</li>
</ul>
<br> </br>
<h3> Recommendations </h3>
<ul>
    <li>Continue programming Cineteca Nacional's classic film series.</li>
    <li>Promote films by renowned directors and films nominated or awarded by the Academy and similar film festivals.</li>
    <li>Explore strategies to increase attendance to films from countries with lower average attendance per screening than Mexico.</li>
</ul>
<br> </br>
<h3> Dashboard </h3>
<div class='tableauPlaceholder' id='viz1709666300770' style='position: relative'><noscript><a href='#'><img alt='Cineteca Nacional De México: Asistencia ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Ci&#47;CinetecaNacionalDeMxicoAsistencia&#47;CinetecaNacionalDeMxicoAsistencia&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='CinetecaNacionalDeMxicoAsistencia&#47;CinetecaNacionalDeMxicoAsistencia' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Ci&#47;CinetecaNacionalDeMxicoAsistencia&#47;CinetecaNacionalDeMxicoAsistencia&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='es-ES' /></object></div>                
<br> </br>
<h3> Files: </h3>
<ul>
    <li><a href="https://drive.google.com/file/d/19rAjps4C3xOSuMbQFTsNAbd2tiGgSUcB/view?usp=sharing"> Queries</a>
    <li><a href="https://drive.google.com/drive/folders/1x4DYx-07bMT2_mKWjpEdB-1NfKTPZEat?usp=sharing"> Data</a>
</ul>
