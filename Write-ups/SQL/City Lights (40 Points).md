# City Lights

![Category](http://img.shields.io/badge/Category-SQL-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-40-brightgreen?style=for-the-badge)

## Details

>De Monne wants to know how many branch offices were included in the database leak. This can be found by figuring out how many unique cities the employees live in. Submit the flag as `flag{#}`.
> 
> Use the MySQL database dump from Body Count.
---

It should be possible to use the query `SELECT COUNT(DISTINCT(city)) FROM employees;` which produced a count of `450`

```
MariaDB [demonne]> select COUNT(DISTINCT(city)) from employees;
+-----------------------+
| COUNT(DISTINCT(city)) |
+-----------------------+
|                   450 |
+-----------------------+
1 row in set (0.008 sec)

```

But this was not the correct flag!?!

When I ran the command without the `COUNT()` function, `SELECT DISTINCT(city) FROM employees;`, I noticed some dupliacte entries in the list?!

```
MariaDB [demonne]> select DISTINCT(city) from employees;
+-------------------+
| city              |
+-------------------+
| Vancouver         |
| Pittsburgh        |
| Baltimore         |
| Bradenton         |
| Nashville         |
| Redwood City      |
| Paterson          |
| Springfield       |
| Phoenix           |
| Fort Worth        |
| Washington        |
| Saint Cloud       |
| Buffalo           |
| Philadelphia      |
| Palmdale          |
| Detroit           |
| Salt Lake City    |
| Garden Grove      |
| Youngstown        |
| Sioux Falls       |
| Pasadena          |
| Houston           |
| Huntington        |
| San Antonio       |
| Rochester         |
| Pompano Beach     |
| Chicago           |
| Aurora            |
| Norwalk           |
| Memphis           |
| Daytona Beach     |
| Long Beach        |
| Herndon           |
| New Brunswick     |
| Tulsa             |
| Montgomery        |
| Englewood         |
| Ocala             |
| Stockton          |
| Birmingham        |
| Greeley           |
| Lexington         |
| Dallas            |
| Greensboro        |
| New Orleans       |
| Naples            |
| Jersey City       |
| Roanoke           |
| Saint Louis       |
| Ogden             |
| Newton            |
| Santa Ana         |
| Charlotte         |
| Saint Paul        |
| Wilkes Barre      |
| Baton Rouge       |
| Gainesville       |
| Honolulu          |
| Kansas City       |
| Portland          |
| Bethesda          |
| Annapolis         |
| Monticello        |
| Charlottesville   |
| Lynchburg         |
| Grand Rapids      |
| Oklahoma City     |
| Louisville        |
| Huntsville        |
| Bethlehem         |
| Santa Monica      |
| Helena            |
| White Plains      |
| Jackson           |
| Florence          |
| Anniston          |
| Mesquite          |
| Sparks            |
| Duluth            |
| Port Washington   |
| Bakersfield       |
| Portsmouth        |
| Minneapolis       |
| Syracuse          |
| Los Angeles       |
| Independence      |
| Plano             |
| Pensacola         |
| Hartford          |
| Denver            |
| Warren            |
| El Paso           |
| Arlington         |
| Amarillo          |
| San Diego         |
| Jamaica           |
| Las Vegas         |
| Pomona            |
| Fort Myers        |
| Saginaw           |
| Wilmington        |
| New York City     |
| Reno              |
| Indianapolis      |
| Boca Raton        |
| Sacramento        |
| Lima              |
| Beaumont          |
| Brea              |
| Corpus Christi    |
| Worcester         |
| Lake Charles      |
| Atlanta           |
| 
New Haven        |
| Richmond          |
| Tacoma            |
| Lakewood          |
| Scottsdale        |
| Lancaster         |
| Camden            |
| Topeka            |
| Miami             |
| Odessa            |
| Southfield        |
| Jacksonville      |
| Mobile            |
| Providence        |
| Seminole          |
| Dayton            |
| Erie              |
| Sioux City        |
| Beaverton         |
| Trenton           |
| Torrance          |
| New Haven         |
| Tucson            |
| Vero Beach        |
| Des Moines        |
| Spartanburg       |
| Lansing           |
| Boise             |
| Irving            |
| Harrisburg        |
| Austin            |
| Colorado Springs  |
| Fort Wayne        |
| Omaha             |
| Chattanooga       |
| Panama City       |
| Farmington        |
| Brockton          |
| Albuquerque       |
| San Bernardino    |
| Prescott          |
| Tampa             |
| North Las Vegas   |
| Asheville         |
| Columbus          |
| Corona            |
| Norfolk           |
| Huntington Beach  |
| Flint             |
| Seattle           |
| Battle Creek      |
| Milwaukee         |
| Muskegon          |
| Boston            |
| Cleveland         |
| Raleigh           |
| Missoula          |
| Shreveport        |
| Davenport         |
| Cincinnati        |
| Boynton Beach     |
| Brooklyn          |
| Saint Petersburg  |
| Provo             |
| Katy              |
| Mount Vernon      |
| North Hollywood   |
| Orlando           |
| Morgantown        |
| Durham            |
| Orange            |
| Punta Gorda       |
| Berkeley          |
| Peoria            |
| Irvine            |
| Newark            |
| Fort Lauderdale   |
| Madison           |
| Santa Barbara     |
| Alexandria        |
| Denton            |
| San Jose          |
| Joliet            |
| Fort Collins      |
| Spring            |
| Wichita           |
| Winston Salem     |
| Charleston        |
| Montpelier        |
| Metairie          |
| Riverside         |
| Reston            |
| Fresno            |
| Fayetteville      |
| Scranton          |
| Champaign         |
| Virginia Beach    |
| Columbia          |
| Merrifield        |
| Cumming           |
| Petaluma          |
| Utica             |
| Chesapeake        |
| Inglewood         |
| Saint Joseph      |
| Bronx             |
| Loretto           |
| Oakland           |
| Knoxville         |
| Clearwater        |
| Waltham           |
| Augusta           |
| Garland           |
| San Francisco     |
| Lincoln           |
| Elizabeth         |
| Arvada            |
| Anchorage         |
| York              |
| Bonita Springs    |
| Allentown         |
| Fairbanks         |
| Biloxi            |
| Simi Valley       |
| Fairfax           |
| Round Rock        |
| Evansville        |
| Waterbury         |
| Chula Vista       |
| Hamilton          |
| Fort Smith        |
| Migrate           |
| Lynn              |
| Reading           |
| Sarasota          |
| Stamford          |
| Eugene            |
| Little Rock       |
| Escondido         |
| College Station   |
| Tyler             |
| Glendale          |
| Decatur           |
| Albany            |
| Whittier          |
| South Bend        |
| Bloomington       |
| Las Cruces        |
| Frankfort         |
| Shawnee Mission   |
| Staten Island     |
| Alhambra          |
| Anaheim           |
| Lubbock           |
| Watertown         |
| Monroe            |
| Gaithersburg      |
| Lawrenceville     |
| Lafayette         |
| Danbury           |
| Hampton           |
| Toledo            |
| Mesa              |
| Jefferson City    |
| Gary              |
| Santa Fe          |
| Spokane           |
| Silver Spring     |
| Evanston          |
| Suffolk           |
| Hialeah           |
| Pinellas Park     |
| Tallahassee       |
| Fort Pierce       |
| Spring Hill       |
| Valley Forge      |
| Salem             |
| Anderson          |
| Santa Cruz        |
| Canton            |
| Boulder           |
| Port Charlotte    |
| Green Bay         |
| Palm Bay          |
| Temple            |
| Greenville        |
| Wichita Falls     |
| Chandler          |
| Lake Worth        |
| Conroe            |
| Aiken             |
| Bryan             |
| Grand Junction    |
| Abilene           |
| Schenectady       |
| Rockford          |
| Longview          |
| Macon             |
| Young America     |
| Midland           |
| West Palm Beach   |
| Salinas           |
| Henderson         |
| Rockville         |
| New Bedford       |
| Terre Haute       |
| Killeen           |
| Lakeland          |
| Idaho Falls       |
| Beaufort          |
| New Castle        |
| San Mateo         |
| Modesto           |
| Littleton         |
| Brooksville       |
| Burbank           |
| Laredo            |
| Apache Junction   |
| South Lake Tahoe  |
| Gadsden           |
| Mc Keesport       |
| Savannah          |
| Humble            |
| Sunnyvale         |
| Bozeman           |
| Athens            |
| Schaumburg        |
| Lees Summit       |
| Waco              |
| Tuscaloosa        |
| Yonkers           |
| Hicksville        |
| Everett           |
| Gilbert           |
| Kingsport         |
| Saint Augustine   |
| Norman            |
| Cheyenne          |
| Woburn            |
| Ventura           |
| Pueblo            |
| Grand Forks       |
| Iowa City         |
| Muncie            |
| Sterling          |
| Santa Clara       |
| Lehigh Acres      |
| Great Neck        |
| Levittown         |
| Des 
Moines       |
| Carson City       |
| Akron             |
| Bellevue          |
| Johnstown         |
| Carol Stream      |
| Gastonia          |
| Palo Alto         |
| London            |
| Racine            |
| Marietta          |
| North Little Rock |
| Cedar Rapids      |
| Juneau            |
| Kalamazoo         |
| Texarkana         |
| Hayward           |
| Billings          |
| Bowie             |
| Van Nuys          |
| San Angelo        |
| High Point        |
| Visalia           |
| Edmond            |
| Fullerton         |
| Galveston         |
| Mountain View     |
| Flushing          |
| 
Sacramento       |
| Fargo             |
| Delray Beach      |
| Ashburn           |
| Largo             |
| Fairfield         |
| Alpharetta        |
| Frederick         |
| Hollywood         |
| San Rafael        |
| Tempe             |
| Concord           |
| Oxnard            |
| Newport News      |
| Maple Plain       |
| Zephyrhills       |
| Manassas          |
| Gulfport          |
| Laurel            |
| Cambridge         |
| Johnson City      |
| Pocatello         |
| Cape Coral        |
| Waterloo          |
| Homestead         |
| Kent              |
| Port Saint Lucie  |
| Ann Arbor         |
| West Hartford     |
| 
Kansas City      |
| Jersey 
City      |
| Gatesville        |
| Dulles            |
| Appleton          |
| Olympia           |
| Murfreesboro      |
| 
Boca Raton       |
| Manchester        |
| Santa Rosa        |
| North Port        |
| Bismarck          |
| Oceanside         |
| Yakima            |
| Myrtle Beach      |
| Valdosta          |
| Moreno Valley     |
| Meridian          |
| Hyattsville       |
| Naperville        |
| Fredericksburg    |
| Northridge        |
| Miami Beach       |
| Vienna            |
| Winter Haven      |
| Troy              |
| Jeffersonville    |
| Bridgeport        |
| Falls Church      |
| San Luis Obispo   |
| East Saint Louis  |
+-------------------+
```

I tried for some time to get the SQL query to provide the correct results, but in the end decided it was likley there was some additional whitepasce or strange charcter encoding causing the issues to decided insteed it was easiser to remove the duplicates manually!

After manualy removing the duplicates from the list above I came up with the corect count of `444`

so the correct flag was;

## flag{444}
