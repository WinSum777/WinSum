# What is this?Limitinit �̪̜̳̣͏�̡͚̺͖̣͈̬̥̀ͮ͂͋ͨ́̄͑͌́̍̊̊̆̋̄̀͠͠͠͠҉̴̷̨̡̢̢́̀͘͢J͊̊ͩ̂ͬ̎́͑̋ͬ͒͆ͯ̌ͭ̋̿ͦͩ҉̶̛̕͘̕͟͏̷̵̵̢̀̀͘͜͡͝͡K̘̬̮̓ͨ̔͗̔͑͘͞͏̨̡͢͢͜͝͝͝o̴̷̞̰̩̣̩͚̻̞̩̱̝̲̦ͩͬ͒͑̉ͤ̊̐͛ͥ̽̚͝͡͠R̷̴̡̨̛͇̖̺͚̲̞̠̜̳͚͊ͩͣ̌ͪ̔ͯ̂́̀͘͘͟͟͝͝ͅḛ̗̓ͥ͐͐ͫ͌̃̏́ͤ1̴̴̸̴̴̨̨͆̑ͦͭ͆͑͛͋̑ͯ̕̕͟͟͡͡3͕͙̜̭̥̞̜͙̖̬̯̻͚̮͎͙̼̔ͯͪͅ͏̵̵̢̧́͜͢͟͡҉̢́́̕͢Explore
WiGLE API
 3.1 
/swagger.json
Search, upload, and integrate statistics from WiGLE. Use API Name+Token from https://wigle.net/account

arkasha, bobzilla and uhtu - Website
Send email to arkasha, bobzilla and uhtu
Interaction with the system is governed by our EULA.
Schemes

HTTPS
Authorize
Bluetooth search and information tools

GET
​/api​/v2​/bluetooth​/detail
Get details and observation records for a single network.

GET
​/api​/v2​/bluetooth​/search
Search the WiGLE Bluetooth database.

Cell search and information tools

GET
​/api​/v2​/cell​/mccMnc
Get MCC and MNC codes for Cellular networks
GET
​/api​/v2​/cell​/search
Search the WiGLE Cell database.

Network density ageing history tools

GET
​/api​/v3​/density​/wifi
Get historical densities of WiFi networks first-seen and most-recently-seen for a geo-quad in one-year buckets.

Network observation file upload and status.

GET
​/api​/v2​/file​/kml​/{transid}
Download a KML summary of a file

GET
​/api​/v2​/file​/transactions
Get the status of files uploaded by the current user

POST
​/api​/v2​/file​/upload
Upload a file
Network search and information tools

POST
​/api​/v2​/network​/comment
Add a comment to a network

GET
​/api​/v2​/network​/detail
Get details and observation records for a single wifi or cell network

GET
​/api​/v2​/network​/geocode
Get coordinates for an address for use in searching

GET
​/api​/v2​/network​/search
Search the WiGLE Wifi database.

Statistics and information

GET
​/api​/v2​/stats​/countries
Get statistics organized by country
GET
​/api​/v2​/stats​/general
Get a named map of general upload statistics
GET
​/api​/v2​/stats​/group
Get group standings
GET
​/api​/v2​/stats​/regions
Get statistics for a specified country, organized by region, postal code, and encryption
GET
​/api​/v2​/stats​/site
Get a named map of site-level statistics
GET
​/api​/v2​/stats​/standings
Get user standings
GET
​/api​/v2​/stats​/user
Get user statistics

Stats group management

GET
​/api​/v2​/group​/admin
Get group info as a stats group administrator
GET
​/api​/v2​/group​/groupEventStats​/{groupId}
Get group member stats for a time-bounded event
GET
​/api​/v2​/group​/groupForUser​/{userName}
Get group (if present) for a user
GET
​/api​/v2​/group​/groupMembers
Get group members
User profile operations

GET
​/api​/v2​/profile​/apiToken
Get all authorization tokens for the logged-in user

GET
​/api​/v2​/profile​/user
Get the user object for the current logged-in user

v3 ALPHA

GET
​/api​/v3​/cellChannel​/{type}
Request list of channels for GSM, LTE, WCDMA, or 5G NR transmitters in specified region

GET
​/api​/v3​/detail​/bt​/{btNetworkId}
Request detail for a bluetooth network

GET
​/api​/v3​/detail​/cell​/{type}​/{operator}​/{lac}​/{cid}
Request detail for a GSM, LTE, WCDMA, or 5G NR network

GET
​/api​/v3​/detail​/cell​/CDMA​/{sid}​/{nid}​/{bsid}
Request detail for a CDMA network

GET
​/api​/v3​/detail​/wifi​/{wifiNetworkId}
Request detail for a WiFi network

Models
NetSearchResponse
WiFiNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
type	string
capabilities	[...]
userfound	boolean
device	integer($int32)
mfgrId	integer($int64)
name	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
CellSiteChannel{
channel	integer($int64)
latitude	number
longitude	number
qos	integer($int32)
}
ChannelDetailResponse{
success	boolean
resultsExceedLimit	boolean
results	[...]
resultType	string
}
MccMncRecord{
type	string
countryName	string
countryCode	string
mcc	string
mnc	string
brand	string
operator	string
status	string
bands	string
notes	string
}
CellSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
GenericNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
id	string
attributes	string
channel	integer($int32)
gentype	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
DensityAsOfDate{
date	string
firstTimeSeenDensity	integer($int64)
lastTimeSeenDensity	integer($int64)
}
DensityResponse{
histogramByCell	[...]
cells	integer($int32)
millisecondsToCalculate	integer($int64)
requestTopLat	number
requestBottomLat	number
requestLeftLon	number
requestRightLon	number
}
GeoHistogram{
topLat	number
bottomLat	number
leftLon	number
rightLon	number
densities	[...]
}
BluetoothLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
type	string
attributes	string
}
BtDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
capabilities	[...]
deviceType	integer($int32)
readOnly: true
locationClusters	[...]
}
BtLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
StreetAddress{
housenumber	string
road	string
city	string
region	string
country	string
postalcode	string
}
WiFiDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
comment	string
readOnly: true
bcninterval	integer($int32)
readOnly: true
freenet	string
readOnly: true
dhcp	string
readOnly: true
paynet	string
readOnly: true
encryption	string
readOnly: true
channel	integer($int32)
readOnly: true
locationClusters	[...]
}
WiFiLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
name	string
netId	string
noise	number($float)
snr	number($float)
wep	string
channel	integer($int32)
frequency	integer($int32)
encryptionValue	string
}
WiFiLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
CellDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
type	string
readOnly: true
attributes	[...]
channel	integer($int32)
readOnly: true
locationClusters	[...]
xarfcn	integer($int32)
readOnly: true
}
CellLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
GenericLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
genType	string
attributes	string
channel	integer($int32)
}
Group{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
authType	string
groupOwner	boolean
}
GroupMember{
groupId	string
username	string
status	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
firstTransid	string
lastTransid	string
monthCount	integer($int64)
prevMonthCount	integer($int64)
}
GroupResponse{
success	boolean
groupid	string
group	Group{...}
users	[...]
}
GroupMemberResponse{
success	boolean
users	[...]
group	Group{...}
}
GroupMemberEventStats{
userName	string
wifiDiscoveredWithLocation	integer($int64)
wifiDiscovered	integer($int64)
cellDiscoveredWithLocation	integer($int64)
cellDiscovered	integer($int64)
btDiscoveredWithLocation	integer($int64)
btDiscovered	integer($int64)
}
GroupStatsResponse{
overAllGroupStats	[...]
startDateTime	string($date-time)
endDateTime	string($date-time)
eventMemberStats	[...]
}
GeocodingResponse{
address	{...}
lat	number
lon	number
importance	number
place_id	integer($int64)
licence	string
osm_type	string
display_name	string
boundingbox	[...]
}
WiFiNetworkDetailResponse{
success	boolean
cdma	boolean
gsm	boolean
lte	boolean
nr	boolean
wcdma	boolean
wifi	boolean
addresses	[...]
results	[...]
}
WiFiNetworkWithLocation{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
locationData	[...]
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
NetworkGeocodingResponse{
success	boolean
results	[...]
}
NetCommentResponse{
success	boolean
comment	string
netid	string
}
Person{
userid	string
email	string
donate	string
joindate	string($date-time)
lastlogin	string($date-time)
flags	integer($int64)
emailVerified	boolean
nextlogin	string($date-time)
session	string
admin	boolean
success	string
}
AuthToken{
authName	string
token	string
status	string
Enum:
Array [ 2 ]
type	string
Enum:
Array [ 5 ]
personId	integer($int64)
}
ResettableAuthTokenResponse{
success	boolean
result	[...]
digest	string
id	integer($int32)
}
GroupStat{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
members	integer($int64)
joined	boolean
groupOwner	boolean
}
GroupStatResponse{
success	boolean
groups	[...]
}
CountriesResponse{
success	boolean
countries	[...]
}
CountryStat{
country	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
EncryptionStat{
wep	string
count	integer($int64)
}
PostalStat{
postalCode	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
RegionResponse{
success	boolean
regions	[...]
postalCode	[...]
encryption	[...]
}
RegionStat{
region	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
UserStandings{
rank	integer($int64)
monthRank	integer($int64)
userName	string
discoveredWiFiGPS	integer($int64)
discoveredWiFiGPSPercent	number($float)
discoveredWiFi	integer($int64)
discoveredCellGPS	integer($int64)
discoveredCell	integer($int64)
discoveredBtGPS	integer($int64)
discoveredBt	integer($int64)
eventMonthCount	integer($int64)
eventPrevMonthCount	integer($int64)
prevRank	integer($int64)
prevMonthRank	integer($int64)
totalWiFiLocations	integer($int64)
first	string
last	string
self	boolean
}
UserStatsResponse{
success	boolean
imageBadgeUrl	string
statistics	UserStandings{...}
rank	integer($int64)
monthRank	integer($int64)
user	string
}
TransLog{
transid	string
username	string
firstTime	string($date-time)
lastupdt	string($date-time)
fileName	string
fileSize	integer($int64)
fileLines	integer($int64)
status	string
discoveredGps	integer($int64)
discovered	integer($int64)
total	integer($int64)
totalGps	integer($int64)
totalLocations	integer($int64)
percentDone	number($float)
timeParsing	integer($int64)
genDiscovered	integer($int64)
genDiscoveredGps	integer($int64)
genTotal	integer($int64)
genTotalGps	integer($int64)
genTotalLocations	integer($int64)
btDiscovered	integer($int64)
btDiscoveredGps	integer($int64)
btTotal	integer($int64)
btTotalGps	integer($int64)
btTotalLocations	integer($int64)
wwwdStatus	string
wait	integer($int64)
brand	string
model	string
osRelease	string
}
TranslogResponse{
success	boolean
results	[...]
processingQueueDepth	integer($int64)
geoQueueDepth	integer($int64)
trilaterationQueueDepth	integer($int64)
}
TransidResponse{
file	string
size	integer($int64)
transId	string
}
UploadResponse{
success	boolean
warning	string
results	UploadResultsResponse{...}
observer	string
}
UploadResultsResponse{
timeTaken	string
filesize	integer($int64)
filename	string
transids	[...]
}
ErrorMessageResponse{
success	boolean
message	string
}Explore
WiGLE API
 3.1 
/swagger.json
Search, upload, and integrate statistics from WiGLE. Use API Name+Token from https://wigle.net/account

arkasha, bobzilla and uhtu - Website
Send email to arkasha, bobzilla and uhtu
Interaction with the system is governed by our EULA.
Schemes

HTTPS
Authorize
Bluetooth search and information tools

GET
​/api​/v2​/bluetooth​/detail
Get details and observation records for a single network.

GET
​/api​/v2​/bluetooth​/search
Search the WiGLE Bluetooth database.

Cell search and information tools

GET
​/api​/v2​/cell​/mccMnc
Get MCC and MNC codes for Cellular networks
GET
​/api​/v2​/cell​/search
Search the WiGLE Cell database.

Network density ageing history tools

GET
​/api​/v3​/density​/wifi
Get historical densities of WiFi networks first-seen and most-recently-seen for a geo-quad in one-year buckets.

Network observation file upload and status.

GET
​/api​/v2​/file​/kml​/{transid}
Download a KML summary of a file

GET
​/api​/v2​/file​/transactions
Get the status of files uploaded by the current user

POST
​/api​/v2​/file​/upload
Upload a file
Network search and information tools

POST
​/api​/v2​/network​/comment
Add a comment to a network

GET
​/api​/v2​/network​/detail
Get details and observation records for a single wifi or cell network

GET
​/api​/v2​/network​/geocode
Get coordinates for an address for use in searching

GET
​/api​/v2​/network​/search
Search the WiGLE Wifi database.

Statistics and information

GET
​/api​/v2​/stats​/countries
Get statistics organized by country
GET
​/api​/v2​/stats​/general
Get a named map of general upload statistics
GET
​/api​/v2​/stats​/group
Get group standings
GET
​/api​/v2​/stats​/regions
Get statistics for a specified country, organized by region, postal code, and encryption
GET
​/api​/v2​/stats​/site
Get a named map of site-level statistics
GET
​/api​/v2​/stats​/standings
Get user standings
GET
​/api​/v2​/stats​/user
Get user statistics

Stats group management

GET
​/api​/v2​/group​/admin
Get group info as a stats group administrator
GET
​/api​/v2​/group​/groupEventStats​/{groupId}
Get group member stats for a time-bounded event
GET
​/api​/v2​/group​/groupForUser​/{userName}
Get group (if present) for a user
GET
​/api​/v2​/group​/groupMembers
Get group members
User profile operations

GET
​/api​/v2​/profile​/apiToken
Get all authorization tokens for the logged-in user

GET
​/api​/v2​/profile​/user
Get the user object for the current logged-in user

v3 ALPHA

GET
​/api​/v3​/cellChannel​/{type}
Request list of channels for GSM, LTE, WCDMA, or 5G NR transmitters in specified region

GET
​/api​/v3​/detail​/bt​/{btNetworkId}
Request detail for a bluetooth network

GET
​/api​/v3​/detail​/cell​/{type}​/{operator}​/{lac}​/{cid}
Request detail for a GSM, LTE, WCDMA, or 5G NR network

GET
​/api​/v3​/detail​/cell​/CDMA​/{sid}​/{nid}​/{bsid}
Request detail for a CDMA network

GET
​/api​/v3​/detail​/wifi​/{wifiNetworkId}
Request detail for a WiFi network

Models
NetSearchResponse
WiFiNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
type	string
capabilities	[...]
userfound	boolean
device	integer($int32)
mfgrId	integer($int64)
name	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
CellSiteChannel{
channel	integer($int64)
latitude	number
longitude	number
qos	integer($int32)
}
ChannelDetailResponse{
success	boolean
resultsExceedLimit	boolean
results	[...]
resultType	string
}
MccMncRecord{
type	string
countryName	string
countryCode	string
mcc	string
mnc	string
brand	string
operator	string
status	string
bands	string
notes	string
}
CellSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
GenericNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
id	string
attributes	string
channel	integer($int32)
gentype	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
DensityAsOfDate{
date	string
firstTimeSeenDensity	integer($int64)
lastTimeSeenDensity	integer($int64)
}
DensityResponse{
histogramByCell	[...]
cells	integer($int32)
millisecondsToCalculate	integer($int64)
requestTopLat	number
requestBottomLat	number
requestLeftLon	number
requestRightLon	number
}
GeoHistogram{
topLat	number
bottomLat	number
leftLon	number
rightLon	number
densities	[...]
}
BluetoothLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
type	string
attributes	string
}
BtDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
capabilities	[...]
deviceType	integer($int32)
readOnly: true
locationClusters	[...]
}
BtLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
StreetAddress{
housenumber	string
road	string
city	string
region	string
country	string
postalcode	string
}
WiFiDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
comment	string
readOnly: true
bcninterval	integer($int32)
readOnly: true
freenet	string
readOnly: true
dhcp	string
readOnly: true
paynet	string
readOnly: true
encryption	string
readOnly: true
channel	integer($int32)
readOnly: true
locationClusters	[...]
}
WiFiLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
name	string
netId	string
noise	number($float)
snr	number($float)
wep	string
channel	integer($int32)
frequency	integer($int32)
encryptionValue	string
}
WiFiLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
CellDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
type	string
readOnly: true
attributes	[...]
channel	integer($int32)
readOnly: true
locationClusters	[...]
xarfcn	integer($int32)
readOnly: true
}
CellLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
GenericLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
genType	string
attributes	string
channel	integer($int32)
}
Group{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
authType	string
groupOwner	boolean
}
GroupMember{
groupId	string
username	string
status	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
firstTransid	string
lastTransid	string
monthCount	integer($int64)
prevMonthCount	integer($int64)
}
GroupResponse{
success	boolean
groupid	string
group	Group{...}
users	[...]
}
GroupMemberResponse{
success	boolean
users	[...]
group	Group{...}
}
GroupMemberEventStats{
userName	string
wifiDiscoveredWithLocation	integer($int64)
wifiDiscovered	integer($int64)
cellDiscoveredWithLocation	integer($int64)
cellDiscovered	integer($int64)
btDiscoveredWithLocation	integer($int64)
btDiscovered	integer($int64)
}
GroupStatsResponse{
overAllGroupStats	[...]
startDateTime	string($date-time)
endDateTime	string($date-time)
eventMemberStats	[...]
}
GeocodingResponse{
address	{...}
lat	number
lon	number
importance	number
place_id	integer($int64)
licence	string
osm_type	string
display_name	string
boundingbox	[...]
}
WiFiNetworkDetailResponse{
success	boolean
cdma	boolean
gsm	boolean
lte	boolean
nr	boolean
wcdma	boolean
wifi	boolean
addresses	[...]
results	[...]
}
WiFiNetworkWithLocation{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
locationData	[...]
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
NetworkGeocodingResponse{
success	boolean
results	[...]
}
NetCommentResponse{
success	boolean
comment	string
netid	string
}
Person{
userid	string
email	string
donate	string
joindate	string($date-time)
lastlogin	string($date-time)
flags	integer($int64)
emailVerified	boolean
nextlogin	string($date-time)
session	string
admin	boolean
success	string
}
AuthToken{
authName	string
token	string
status	string
Enum:
Array [ 2 ]
type	string
Enum:
Array [ 5 ]
personId	integer($int64)
}
ResettableAuthTokenResponse{
success	boolean
result	[...]
digest	string
id	integer($int32)
}
GroupStat{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
members	integer($int64)
joined	boolean
groupOwner	boolean
}
GroupStatResponse{
success	boolean
groups	[...]
}
CountriesResponse{
success	boolean
countries	[...]
}
CountryStat{
country	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
EncryptionStat{
wep	string
count	integer($int64)
}
PostalStat{
postalCode	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
RegionResponse{
success	boolean
regions	[...]
postalCode	[...]
encryption	[...]
}
RegionStat{
region	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
UserStandings{
rank	integer($int64)
monthRank	integer($int64)
userName	string
discoveredWiFiGPS	integer($int64)
discoveredWiFiGPSPercent	number($float)
discoveredWiFi	integer($int64)
discoveredCellGPS	integer($int64)
discoveredCell	integer($int64)
discoveredBtGPS	integer($int64)
discoveredBt	integer($int64)
eventMonthCount	integer($int64)
eventPrevMonthCount	integer($int64)
prevRank	integer($int64)
prevMonthRank	integer($int64)
totalWiFiLocations	integer($int64)
first	string
last	string
self	boolean
}
UserStatsResponse{
success	boolean
imageBadgeUrl	string
statistics	UserStandings{...}
rank	integer($int64)
monthRank	integer($int64)
user	string
}
TransLog{
transid	string
username	string
firstTime	string($date-time)
lastupdt	string($date-time)
fileName	string
fileSize	integer($int64)
fileLines	integer($int64)
status	string
discoveredGps	integer($int64)
discovered	integer($int64)
total	integer($int64)
totalGps	integer($int64)
totalLocations	integer($int64)
percentDone	number($float)
timeParsing	integer($int64)
genDiscovered	integer($int64)
genDiscoveredGps	integer($int64)
genTotal	integer($int64)
genTotalGps	integer($int64)
genTotalLocations	integer($int64)
btDiscovered	integer($int64)
btDiscoveredGps	integer($int64)
btTotal	integer($int64)
btTotalGps	integer($int64)
btTotalLocations	integer($int64)
wwwdStatus	string
wait	integer($int64)
brand	string
model	string
osRelease	string
}
TranslogResponse{
success	boolean
results	[...]
processingQueueDepth	integer($int64)
geoQueueDepth	integer($int64)
trilaterationQueueDepth	integer($int64)
}
TransidResponse{
file	string
size	integer($int64)
transId	string
}
UploadResponse{
success	boolean
warning	string
results	UploadResultsResponse{...}
observer	string
}
UploadResultsResponse{
timeTaken	string
filesize	integer($int64)
filename	string
transids	[...]
}
ErrorMessageResponse{
success	boolean
message	string
}Toggle navigation
home
WiGLE CSV Format v1.6

WiGLE has adopted a simple modified comma-separated-value (CSV) format for wireless network observation upload through it's client as well as for a data interchange format. This is simple, mostly-human-readable format that allows us to reliably accept data from multiple software packages. The WiGLE CSV format adheres to UTF-8 encoded rfc4180 for the most part, however we require a pre-header row containing client specification before the CSV-standard header definition. The pre-header is also rfc4180 escaped. Most full-featured CSV generators/parsers can be set to prepend/ignore this row by default.
Pre-header (Device and planetary location)
Description
[Format version],appRelease=[version],model=[device model],release=[device release],device=[device name],display=[device display characteristics],board=[device board descriptor],brand=[device brand],star=[system star],body=[orbiting body index],subBody=[orbit index of sub-body]
Example
WigleWifi-1.6,appRelease=2.78,model=X-37B,release=11.0.0,device=felgercarb,display=OPSPLS1.76-1-S,board=snodgrass,"brand=Moog, LLC",star=Sol,body=4,subBody=0
Details
Field Name	Description	Example
Format version	Current format - treat this as fixed for the version you've selected to implement	WigleWifi-1.6
appRelease	The current release of the application creating this CSV	2.53
model	The device model measuring these signals	X-37B
release	The device OS version	11.0.0
device	The device name/codename	felgercarb
display	The device display if present	OPSPLS1.76-1-S
board	The device core circuit board/processor version	snodgrass
brand	The device brand	Moog, LLC
star	The star around which these points were observed	Sol(only ""Sol is supported)
body	The body's orbit index about the star	4 (Sol 4,0 is Mars)
subBody	The the satellite orbit index applicable, otherwise 0	1 (Sol 3,1 is the Earth's moon)
NOTE: While we're aware that star,body,subBody notation in the header prevents multiple bodies/subbodies per file, current positioning technology and travel speeds make this a reasonable assumption. We may revisit this in subsequent revisions.

Header
Description/Example
MAC,SSID,AuthMode,FirstSeen,Channel,Frequency,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,RCOIs,MfgrId,Type

The header is a fixed ordered set describing the columns following. It is somewhat overloaded to accommodate cell (both CDMA and GSM variants) and Bluetooth, but has been maintained for purposes of backward compatibility.

WiFi Rows
Description
[BSSID],[SSID],[Capabilities],[First timestamp seen],[Channel],[Frequency],[RSSI],[Latitude],[Longitude],[Altitude],[Accuracy],[RCOIs],[MfgrId],[Type]
Example
1a:9f:ee:5c:71:c6,Scampoodle,[WPA2-EAP-CCMP][ESS],2018-08-01 13:08:27,161,5805,-43,37.76578028,-123.45919439,67,3.2160000801086426,5A03BA0000 BAA2D00000 BAA2D02000,,WIFI
Details
Field Name	Description	Example
BSSID	Basic Service Set Identifier - hardware address	1a:9f:ee:5c:71:c6
SSID	Service Set Identifier - the access point name	Scampoodle
Capabilities	Capabilities array as specified by package. Based on Android capabilities sets.	[WPA2-EAP-CCMP][ESS]
First timestamp seen	First timestamp seen in SQL seconds-precision time format (YYYY-MM-DD hh:mm:ss), assumes UTC	2018-08-01 13:08:27
Channel	Integer channel value for the observed signal	161
Frequency	Integer center frequency value in MHz for the observed signal	5805
RSSI	Received Signal Strength Indicator (RSSI) as reported by the radio	-43
Latitude	Observed latitude in decimal (degrees.decimal degrees) format	37.76578028
Longitude	Observed longitude in decimal (degrees.decimal degrees) format	-123.45919439
Altitude	Estimated position altitude in integer meters	67
Accuracy	Estimated position accuracy in decimal meters	3.2160000801086426
RCOIs	Roaming Consortium Organizational Identifiers, space delimited	5A03BA0000 BAA2D00000 BAA2D02000
MfgrId	(left blank)	(left blank)
Type	The device type - always WIFI for WiFi networks currently	WIFI
Cell Rows
Description
[Cell Key],[Network Name],[Capabilities],[First timestamp seen],[Channel],[Frequency],[RSSI],[Latitude],[Longitude],[Altitude],[Accuracy],[RCOIs],[MfgrId],[Type]
Example
310410_56967_4118917,AT&T Mobility,WCDMA;310410,2018-08-03 18:14:15,,4385,-81,37.72090053,-122.44579219,104,34.30400085449219,,,WCDMA
Details
Field Name	Description	Example
Cell Key	Composite Identifier - depends on network type:
For CDMA:[System]_[Network]_[Base Station]
For GSM:[Operator*]_[LAC]_[Cell ID]
For WCDMA:[Operator*]_[LAC]_[Cell ID]
For LTE:[Operator*]_[LAC]_[Cell ID]
For NR:[Operator*]_[LAC]_[Cell ID]


*Operator: for GSM-derived networks this is MCCMNCconcatenated to a 6 digit format. MCC and MNC are searchable through the WiGLE API via the https://api.wigle.net/api/v2/cell/mccMnc endpoint.	310410_56967_4118917
Network Name	For GSM/WCDMA/LTE/NR: reported MCCMNC lookup value if available, otherwise reported network name from radio/SIM. For CDMA: reported network name from radio.	AT&T Mobility
Capabilities	For GSM/WCDMA/LTE/NR: Network type + ; + MCC+MNC (operator value)
For CDMA: Network type + ; + System	WCDMA;310410
First timestamp seen	First timestamp seen in SQL seconds-precision time format (YYYY-MM-DD hh:mm:ss), assumes UTC	2018-08-01 13:08:27
Channel	(left blank)	(left blank)
Frequency	Integer center frequency value depending on network type:
For CDMA:0
For GSM:Observed ARFCN
For WCDMA:Observed UARFCN
For LTE:Observed EARFCN
For NR:Observed NRARFCN
4385
RSSI	Received Signal Strength Indicator (RSSI) as reported by the radio	-81
Latitude	Observed latitude in decimal (degrees.decimal degrees) format	37.72090053
Longitude	Observed longitude in decimal (degrees.decimal degrees) format	-122.44579219
Altitude	Estimated position altitude in integer meters	104
Accuracy	Estimated position accuracy in decimal meters	34.30400085449219
RCOIs	(left blank)	(left blank)
MfgrId	(left blank)	(left blank)
Type	The device type - always one of CDMA, WCDMA, GSM, LTE, or NR.	WCDMA
Bluetooth Rows
Description
[BD_ADDR],[Device Name],[Capabilities],[First timestamp seen],[Channel],[Frequency],[RSSI],[Latitude],[Longitude],[Altitude],[Accuracy],[RCOIs],[MfgrId],[Type]
Example
63:56:ac:c4:d4:30,,Misc [LE],2018-08-03 18:14:12,0,,-67,37.76090571,-122.44877987,104,49.3120002746582,,72,BLE
Details
Field Name	Description	Example
BD_ADDR	Bluetooth Device Address - hardware address	1a:9f:ee:5c:71:c6
Device Name	The published name of the Bluetooth device if available	Jabra Headset
Capabilities	List; includes the device type list if provided, and optionally [BT] or [BLE] enclosed in square brackets to describe the first scan type detecting the device.	Misc [LE]
First timestamp seen	First timestamp seen in SQL seconds-precision time format (YYYY-MM-DD hh:mm:ss), assumes UTC	2018-08-01 13:08:27
Channel	0 for Bluetooth devices	0
Frequency	Bluetooth "Device Type" code	7936
RSSI	Received Signal Strength Indicator (RSSI) as reported by the radio	-67
Latitude	Observed latitude in decimal (degrees.decimal degrees) format	37.73090571
Longitude	Observed longitude in decimal (degrees.decimal degrees) format	-122.42877987
Altitude	Estimated position altitude in integer meters	104
Accuracy	Estimated position accuracy in decimal meters	49.3120002746582
RCOIs	(left blank)	(left blank)
MfgrId	The Bluetooth Manufacturer ID, if available. Otherwise blank.	72
Type	The device type - always BT or BLE for Bluetooth or BTLE devices respectively	BLE
Social
Wiki
Mastodon
Bluesky
Twitter
IRC with TLS
Site Information
FAQ
End-User Agreement
Privacy
Our ToDo List
/dev/random
Cafepress Gear
Links
user management
Reset Password
Register
News
Forums
News RSS
Stats RSS
WiGLE respects your privacy. To have records of your access point removed from our database, or if you have any questions or suggestions, send an email to: WiGLE-admin[at]WiGLE.net (please include BSSID (MAC) in removal requests). We're also on IRC with TLS: at WiGLE.net:6668

Copyright 2001-2026 bobzilla && arkasha && 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/apex/com.android.art/javalib/core-oj.jar:/apex/com.android.art/javalib/core-libart.jar:/apex/com.android.art/javalib/okhttp.jar:/apex/com.android.art/javalib/bouncycastle.jar:/apex/com.android.art/javalib/apache-xml.jar:/system/framework/framework.jar:/system/framework/framework-graphics.jar:/system/framework/framework-location.jar:/system/framework/ext.jar:/system/framework/telephony-common.jar:/system/framework/voip-common.jar:/system/framework/ims-common.jar:/system/framework/knoxsdk.jar:/system/framework/framework-platformcrashrecovery.jar:/system/framework/framework-ondeviceintelligence-platform.jar:/system/framework/framework-nfc.jar:/system/framework/tcmiface.jar:/system/framework/telephony-ext.jar:/system/framework/QPerformance.jar:/system/framework/UxPerformance.jar:/system/framework/esecomm.jar:/apex/com.android.i18n/javalib/core-icu4j.jar:/apex/com.android.adservices/javalib/framework-adservices.jar:/apex/com.android.adservices/javalib/framework-sdksandbox.jar:/apex/com.android.appsearch/javalib/framework-appsearch.jar:/apex/com.android.bt/javalib/framework-bluetooth.jar:/apex/com.android.configinfrastructure/javalib/framework-configinfrastructure.jar:/apex/com.android.conscrypt/javalib/conscrypt.jar:/apex/com.android.devicelock/javalib/framework-devicelock.jar:/apex/com.android.healthfitness/javalib/framework-healthfitness.jar:/apex/com.android.ipsec/javalib/android.net.ipsec.ike.jar:/apex/com.android.media/javalib/updatable-media.jar:/apex/com.android.mediaprovider/javalib/framework-mediaprovider.jar:/apex/com.android.mediaprovider/javalib/framework-pdf.jar:/apex/com.android.mediaprovider/javalib/framework-pdf-v.jar:/apex/com.android.mediaprovider/javalib/framework-photopicker.jar:/apex/com.android.ondevicepersonalization/javalib/framework-ondevicepersonalization.jar:/apex/com.android.os.statsd/javalib/framework-statsd.jar:/apex/com.android.permission/javalib/framework-permission.jar:/apex/com.android.permission/javalib/framework-permission-s.jar:/apex/com.android.profiling/javalib/framework-profiling.jar:/apex/com.android.scheduling/javalib/framework-scheduling.jar:/apex/com.android.sdkext/javalib/framework-sdkextensions.jar:/apex/com.android.tethering/javalib/framework-connectivity.jar:/apex/com.android.tethering/javalib/framework-connectivity-b.jar:/apex/com.android.tethering/javalib/framework-connectivity-t.jar:/apex/com.android.tethering/javalib/framework-tethering.jar:/apex/com.android.uwb/javalib/framework-ranging.jar:/apex/com.android.uwb/javalib/framework-uwb.jar:/apex/com.android.virt/javalib/framework-virtualization.jar:/apex/com.android.wifi/javalib/framework-wifi.jar:/apex/com.samsung.android.lifeguard/javalib/framework-lifeguard.jar:/apex/com.samsung.android.shell/javalib/framework-samsung-shell.jarlogEvent('E1', {
    E1P1: 'activitybar',
    ...f1,
    ...f4,
    timer: {
        waited: 536,
        processing: 43,
        queued: 97,
        elasped: 812
    }
});function logEvent(eventName, eventData) {
    eventData.CP1 = getSQMUserId();
    service.sendEvent(eventName, eventData);
}

let f1 : F1 = { F1P1 : 23 };

let f2 : F2 = { F2P1 : document.getLine(1) };
 
let f3 : F3 = { F3P1: publisher.displayName };

let f4 : F4 = {
    F4P1: extension.extensionName,
    F4P2: {
        ...f2,
        ...f3
    }
};

logEvent('E1', {
    E1P1: 'activitybar',
    ...f1,
    ...f4,
    timer: {
        waited: 536,
        processing: 43,
        queued: 97,
        elasped: 812
    }
});// __GDPR__COMMON__ "CP1" : { "endPoint": "SqmUserId", "classification": "EndUserPseudonymizedInformation", "purpose": "BusinessInsight" }
function logEvent(eventName, eventData) {
    eventData.CP1 = getSQMUserId();
    service.sendEvent(eventName, eventData);
}

/* __GDPR__FRAGMENT__
   "F1" : {
      "F1P1": { "classification": "SystemMetaData", "purpose": "FeatureInsight" }
   }
 */
let f1 : F1 = { F1P1 : 23 };

/* __GDPR__FRAGMENT__
   "F2" : {
      "F2P1" : { "classification": "CustomerContent", "purpose": "PerformanceAndHealth" }
   }
 */
let f2 : F2 = { F2P1 : document.getLine(1) };
 
/* __GDPR__FRAGMENT__
   "F3" : {
      "F3P1" : { "classification": "PublicPersonalData", "purpose": "FeatureInsight" }
   }
 */
let f3 : F3 = { F3P1: publisher.displayName };

/* __GDPR__FRAGMENT__
   "F4" : {
      "F4P1" : { "classification": "PublicNonPersonalData", "purpose": "FeatureInsight" },
      "F4P2": { 
          "${inline}": [
              "${F2}",
              "${F3}"
            ] 
        }
   }
 */
let f4 : F4 = {
    F4P1: extension.extensionName,
    F4P2: {
        ...f2,
        ...f3
    }
};

/* __GDPR__
   "E1" : {
      "E1P1" : { "classification": "SystemMetaData", "purpose": "FeatureInsight" },
      "${include}": [ 
          "${F1}",
          "${F4}"
        ],
      "${wildcard}": [
         {
            "${prefix}": "timer.",
            "${classification}": { "classification": "SystemMetaData", "purpose": "FeatureInsight" }
         }
      ]
   }
 */
logEvent('E1', {
    E1P1: 'activitybar',
    ...f1,
    ...f4,
    timer: {
        waited: 536,
        processing: 43,
        queued: 97,
        elasped: 812
    }
});   "E1" : {
      "E1P1" : { "classification": "SystemMetaData", "purpose": "FeatureInsight" },
      "F1P1": { "classification": "SystemMetaData", "purpose": "FeatureInsight" },
      "F4P4" : { "classification": "PublicNonPersonalData", "purpose": "FeatureInsight" },
      "F4P2.F2P1" : { "classification": "CustomerContent", "purpose": "PerformanceAndHealth" },
      "F4P2.F3P1" : { "classification": "PublicPersonalData", "purpose": "FeatureInsight" },
      "${wildcard}": [
         {
            "${prefix}": "timer.",
            "${classification}": { "classification": "SystemMetaData", "purpose": "FeatureInsight" }
         }
      ],
      "CP1" : { "endPoint": "SqmUserId", "classification": "EndUserPseudonymizedInformation", "purpose": "BusinessInsight" }
   }{ 
    endPoint?: "none" | "SqmUserId" | "SqmMachineId",
    classification: "SystemMetaData" | "CustomerContent" | "EndUserPseudonymizedInformation" | "PublicPersonalData" | "PublicNonPersonalData",
    purpose: "FeatureInsight" | "PerformanceAndHealth" | "BusinessInsight" | "SecurityAndAuditing",
    isMeasurement?: Boolean
}side/compactibilities.possibilities/copy.paste/deleteUpper Case,lower case,Capitialism/LFont to RFont/backwards to font/Top to bottom/side to side/compactibilities.possibilities/copy.paste/delete | letsencryptoconfiguration.sysconfig/cmdletsencryptoconfig.daemon system-wide configuration root shell script.sh PJ10aW6MkTMFiQwFAzmgIar2UcSxvz2Heyhf0aNHFTe7c3ZohNefuP0aFGkQ2bE8O34GE62WnzEgLWEKLMHW45bpKOpLiikcFYkHNS0cbbldAZLWmGUKnREs45skZsi8FAokObCXY9vOBPE0b5zL5NtJpQZi8WKpEZNjrkbok5HKUtPF5{"470":{"01":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"01","brand":"Grameenphone","operator":"Grameenphone Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800"},"02":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"02","brand":"Robi","operator":"Axiata Bangladesh Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 900 / LTE 1800","notes":"Formerly Aktel"},"03":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"03","brand":"Banglalink","operator":"Banglalink Digital Communications Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800","notes":"VEON"},"04":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"04","brand":"TeleTalk","operator":"Teletalk Bangladesh Limited","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100"},"05":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"05","brand":"Citycell","operator":"Pacific Bangladesh Telecom Limited","status":"Not operational","bands":"CDMA 800","notes":"Shutdown by Bangladesh Telecommunication Regulatory Commission in 2016"},"07":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"07","brand":"Airtel","operator":"Bharti Airtel Bangladesh Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"Formerly Warid Telcom, later Airtel. Currently merged with Robi keeping brand name Airtel"},"09":{"type":"National","countryName":"Bangladesh","countryCode":"BD","mcc":"470","mnc":"09","brand":"ollo","operator":"Bangladesh Internet Exchange Limited (BIEL)","status":"Operational","bands":"LTE 800 / LTE 2600 / WiMAX 3500"}},"350":{"00":{"type":"National","countryName":"Bermuda","countryCode":"BM","mcc":"350","mnc":"00","brand":"CellOne","operator":"Bermuda Digital Communications Ltd.","status":"Operational","bands":"GSM 1900 / UMTS 850 / LTE 850"},"11":{"type":"National","countryName":"Bermuda","countryCode":"BM","mcc":"350","mnc":"11","operator":"Deltronics","status":"Unknown","bands":"Unknown"},"01":{"type":"National","countryName":"Bermuda","countryCode":"BM","mcc":"350","mnc":"01","brand":"Digicel Bermuda","operator":"Telecommunications (Bermuda & West Indies) Ltd","status":"Reserved","bands":"GSM 1900"},"02":{"type":"National","countryName":"Bermuda","countryCode":"BM","mcc":"350","mnc":"02","brand":"Mobility","operator":"M3 Wireless","status":"Operational","bands":"GSM 1900 / UMTS"},"05":{"type":"National","countryName":"Bermuda","countryCode":"BM","mcc":"350","mnc":"05","operator":"Telecom Networks","status":"Unknown","bands":"Unknown"}},"230":{"99":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"99","brand":"Vodafone","operator":"Vodafone Czech Republic","status":"Operational","bands":"GSM 1800","notes":"R&D Centre at FEE, CTU (educational, experimental)"},"01":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"01","brand":"T-Mobile","operator":"T-Mobile Czech Republic","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600","notes":"former Paegas"},"02":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"02","brand":"O2","operator":"O2 Czech Republic","status":"Operational","bands":"CDMA 450 / GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800","notes":"former Eurotel"},"03":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"03","brand":"Vodafone","operator":"Vodafone Czech Republic","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 900 / LTE 1800 / LTE 2100","notes":"former Oskar"},"04":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"04","operator":"Nordic Telecom s.r.o.","status":"Operational","bands":"MVNO","notes":"former U:fon, Air Telecom; CDMA 420MHz shut down Dec 2017"},"05":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"05","operator":"PODA a.s.","status":"Unknown","bands":"TD-LTE 3700","notes":"Former TRAVEL TELEKOMMUNIKATION"},"06":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"06","operator":"OSNO TELECOMUNICATION, s.r.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"07":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"07","operator":"ASTELNET, s.r.o.","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"08":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"08","operator":"Compatel s.r.o.","status":"Unknown","bands":"Unknown"},"09":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"09","brand":"Vectone Mobile","operator":"Mundio Distribution Czech Republic s.r.o.","status":"Unknown","bands":"MVNO"},"98":{"type":"National","countryName":"Czech Republic","countryCode":"CZ","mcc":"230","mnc":"98","operator":"Správa železniční dopravní cesty, s.o.","status":"Operational","bands":"GSM-R 900","notes":"railways communication"}},"472":{"01":{"type":"National","countryName":"Maldives","countryCode":"MV","mcc":"472","mnc":"01","brand":"Dhiraagu","operator":"Dhivehi Raajjeyge Gulhun","status":"Operational","bands":"GSM 900 / UMTS 2100 / LTE 1800 / LTE 2600"},"02":{"type":"National","countryName":"Maldives","countryCode":"MV","mcc":"472","mnc":"02","brand":"Ooredoo","operator":"Wataniya Telecom Maldives","status":"Operational","bands":"GSM 900 / UMTS 2100 / LTE 2600"}},"352":{"110":{"type":"National","countryName":"Grenada","countryCode":"GD","mcc":"352","mnc":"110","brand":"FLOW","operator":"Cable & Wireless Grenada Ltd.","status":"Operational","bands":"GSM 850"},"030":{"type":"National","countryName":"Grenada","countryCode":"GD","mcc":"352","mnc":"030","brand":"Digicel","operator":"Digicel Grenada Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Also uses MCC 338 MNC 05 (Jamaica)"}},"231":{"99":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"99","brand":"ŽSR","operator":"Železnice Slovenskej Republiky","status":"Operational","bands":"GSM-R","notes":"Railway communication and signalling"},"01":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"01","brand":"Orange","operator":"Orange Slovensko","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 2600","notes":"Former Globtel"},"02":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"02","brand":"Telekom","operator":"Slovak Telekom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former Eurotel"},"03":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"03","brand":"4ka","operator":"SWAN Mobile, a.s.","status":"Operational","bands":"LTE 1800 / TD-LTE 3500 / TD-LTE 3700"},"04":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"04","brand":"Telekom","operator":"Slovak Telekom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"Former T-Mobile"},"05":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"05","brand":"Orange","operator":"Orange Slovensko","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100"},"06":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"06","brand":"O2","operator":"Telefónica O2 Slovakia","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / TD-LTE 3500 / TD-LTE 3700"},"07":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"07","operator":"Towercom, a. s.","status":"Unknown","bands":"Unknown"},"08":{"type":"National","countryName":"Slovakia","countryCode":"SK","mcc":"231","mnc":"08","operator":"IPfon, s.r.o.","status":"Unknown","bands":"Unknown"}},"232":{"22":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"22","operator":"Plintron Austria Limited","status":"Unknown","bands":"MVNO"},"01":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"01","brand":"A1.net","operator":"A1 Telekom Austria","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 2600","notes":"former A1 / Mobilkom / PTA"},"23":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"23","operator":"T-Mobile Austria GmbH","status":"Unknown","bands":"Unknown"},"02":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"02","operator":"A1 Telekom Austria","status":"Reserved"},"03":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"03","brand":"T-Mobile AT","operator":"T-Mobile Austria","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"former Max.Mobil / national roaming agreement with 232-10"},"04":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"04","brand":"T-Mobile AT","operator":"T-Mobile Austria Gmbh","status":"Unknown","bands":"Unknown"},"05":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"05","brand":"3","operator":"Hutchison Drei Austria","status":"Operational","bands":"GSM 900 / UMTS 2100","notes":"owned by Hutchison Drei Austria / former Orange Austria / One / Connect"},"06":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"06","brand":"Orange AT","operator":"Orange Austria GmbH","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"07":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"07","brand":"tele.ring","operator":"T-Mobile Austria","status":"Operational","bands":"MVNO","notes":"brand of T-Mobile Austria"},"08":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"08","brand":"Lycamobile","operator":"Lycamobile Austria","status":"Operational","bands":"MVNO"},"09":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"09","brand":"Tele2Mobil","operator":"A1 Telekom Austria","status":"Operational","bands":"MVNO","notes":"division bought from Tele2 by A1 Telekom Austria; customers \"moved\" to bob (232-11)"},"91":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"91","brand":"GSM-R A","operator":"ÖBB","status":"Operational","bands":"GSM-R","notes":"railways communication"},"92":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"92","brand":"ArgoNET","operator":"ArgoNET GmbH","status":"Operational","bands":"CDMA450 / LTE450","notes":"machine to machine communication for critical infrastructure"},"10":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"10","brand":"3","operator":"Hutchison Drei Austria","status":"Operational","bands":"UMTS 2100 / LTE 900 / LTE 1800 / LTE 2100 / LTE 2600","notes":"national roaming agreement with 232-03, one-way national roaming agreement with 232-01"},"11":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"11","brand":"bob","operator":"A1 Telekom Austria","status":"Operational","bands":"MVNO","notes":"brand of A1 Telekom Austria"},"12":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"12","brand":"yesss!","operator":"A1 Telekom Austria","status":"Operational","bands":"MVNO","notes":"owned by A1 Telekom Austria / one-way national roaming agreement with 232-05"},"13":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"13","brand":"upc","operator":"UPC Austria","status":"Operational","bands":"MVNO"},"14":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"14","operator":"Hutchison Drei Austria","status":"Reserved","bands":"Unknown"},"15":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"15","brand":"Vectone Mobile","operator":"Mundio Mobile Austria","status":"Operational","bands":"MVNO","notes":"former Barablu Mobile Austria, uses A1"},"16":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"16","operator":"Hutchison Drei Austria","status":"Reserved","bands":"Unknown"},"17":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"17","operator":"MASS Response Service GmbH","status":"Unknown","bands":"Unknown"},"18":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"18","operator":"smartspace GmbH","status":"Unknown","bands":"MVNO"},"19":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"19","operator":"Tele2 Telecommunication GmbH","status":"Unknown","bands":"Unknown"},"20":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"20","brand":"m:tel","operator":"MTEL Austrija GmbH","status":"Operational","bands":"MVNO"},"21":{"type":"National","countryName":"Austria","countryCode":"AT","mcc":"232","mnc":"21","operator":"Salzburg AG für Energie, Verkehr und Telekommunikation","status":"Unknown","bands":"Unknown"}},"354":{"860":{"type":"National","countryName":"Montserrat (United Kingdom)","countryCode":"MS","mcc":"354","mnc":"860","brand":"FLOW","operator":"Cable & Wireless","status":"Operational","bands":"GSM 850"}},"234":{"00":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"00","brand":"BT","operator":"BT Group","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100"},"01":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"01","brand":"Vectone Mobile","operator":"Mundio Mobile Limited","status":"Operational","bands":"MVNO","notes":"Previously Mapesbury Communications Ltd.; uses EE network"},"02":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"02","brand":"O2 (UK)","operator":"Telefónica Europe","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / TD-LTE 2300"},"03":{"type":"National","countryName":"Guernsey (United Kingdom)","countryCode":"GG","mcc":"234","mnc":"03","brand":"Airtel-Vodafone","operator":"Guernsey Airtel Ltd","status":"Operational","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800"},"04":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"04","brand":"FMS Solutions Ltd","operator":"FMS Solutions Ltd","status":"Reserved","bands":"GSM 1800"},"05":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"05","operator":"COLT Mobile Telecommunications Limited","status":"Not operational","notes":"MNC withdrawn"},"06":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"06","operator":"Internet Computer Bureau Limited","status":"Not operational","notes":"MNC withdrawn"},"07":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"07","brand":"Vodafone UK","operator":"Vodafone","status":"Not operational","bands":"GSM 1800","notes":"Former Cable & Wireless Worldwide; MNC withdrawn"},"08":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"08","operator":"BT OnePhone (UK) Ltd","status":"Unknown"},"09":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"09","operator":"Tismi BV","status":"Unknown"},"50":{"type":"National","countryName":"Guernsey (United Kingdom)","countryCode":"GG","mcc":"234","mnc":"50","brand":"JT","operator":"JT Group Limited","status":"Operational","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"former Wave Telecom"},"51":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"51","brand":"Relish","operator":"UK Broadband Limited","status":"Operational","bands":"TD-LTE 3500 / TD-LTE 3700"},"52":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"52","operator":"Shyam Telecom UK Ltd","status":"Unknown","bands":"Unknown"},"53":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"53","operator":"Limitless Mobile Ltd","status":"Operational","bands":"MVNO"},"10":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"10","brand":"O2 (UK)","operator":"Telefónica Europe","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / TD-LTE 2300"},"54":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"54","brand":"iD Mobile","operator":"The Carphone Warehouse Limited","status":"Operational","bands":"MVNO","notes":"Uses Three UK"},"55":{"type":"National","countryName":"Guernsey (United Kingdom)","countryCode":"GG","mcc":"234","mnc":"55","brand":"Sure Mobile","operator":"Sure (Guernsey) Limited","status":"Operational","bands":"GSM 900 / UMTS 2100 / LTE 800 / LTE 1800","notes":"former Cable & Wireless"},"11":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"11","brand":"O2 (UK)","operator":"Telefónica Europe","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / TD-LTE 2300"},"12":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"12","brand":"Railtrack","operator":"Network Rail Infrastructure Ltd","status":"Operational","bands":"GSM-R"},"56":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"56","operator":"CESG","status":"Unknown","bands":"Unknown"},"13":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"13","brand":"Railtrack","operator":"Network Rail Infrastructure Ltd","status":"Operational","bands":"GSM-R"},"57":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"57","operator":"Sky UK Limited","status":"Unknown","bands":"Unknown"},"58":{"type":"National","countryName":"Isle of Man (United Kingdom)","countryCode":"IM","mcc":"234","mnc":"58","brand":"Pronto GSM","operator":"Manx Telecom","status":"Operational","bands":"GSM 900 / UMTS 2100 / LTE 800 / LTE 1800"},"14":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"14","brand":"Hay Systems Ltd","operator":"Hay Systems Ltd","status":"Operational","bands":"GSM 1800"},"15":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"15","brand":"Vodafone UK","operator":"Vodafone","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600 / TD-LTE 2600"},"59":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"59","operator":"Limitless Mobile Ltd","status":"Operational","bands":"MVNO"},"16":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"16","brand":"Talk Talk","operator":"TalkTalk Communications Limited","status":"Operational","bands":"MVNO","notes":"Formerly Opal Tel Ltd; uses Vodafone network"},"17":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"17","operator":"FleXtel Limited","status":"Unknown"},"18":{"type":"National","countryName":"Isle of Man (United Kingdom)","countryCode":"IM","mcc":"234","mnc":"18","brand":"Cloud 9 Mobile","operator":"Cloud 9 Mobile Communications PLC","status":"Not operational","bands":"GSM 1800 / UMTS 2100","notes":"Retired"},"19":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"19","brand":"Private Mobile Networks PMN","operator":"Teleware plc","status":"Operational","bands":"GSM 1800","notes":"Private GSM; roaming with Vodafone"},"20":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"20","brand":"3","operator":"Hutchison 3G UK Ltd","status":"Operational","bands":"UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100","notes":"National roaming with Orange (UK)'s 2G network"},"21":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"21","operator":"LogicStar Ltd","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"22":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"22","operator":"Telesign Mobile Limited","status":"Unknown","bands":"Unknown","notes":"Former Routo Telecommunications Limited"},"23":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"23","operator":"Icron Network Limited","status":"Unknown","bands":"Unknown"},"24":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"24","brand":"Greenfone","operator":"Stour Marine Limited","status":"Operational","bands":"MVNO","notes":"Uses Stour Marine network"},"25":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"25","brand":"Truphone","operator":"Truphone","status":"Operational","bands":"MVNO","notes":"Uses Vodafone network"},"26":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"26","brand":"Lycamobile","operator":"Lycamobile UK Limited","status":"Operational","bands":"MVNO","notes":"Uses O2 Network"},"27":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"27","operator":"Teleena UK Limited","status":"Operational","bands":"MVNE"},"28":{"type":"National","countryName":"Jersey (United Kingdom)","countryCode":"JE","mcc":"234","mnc":"28","operator":"Marathon Telecom Limited","status":"Not operational","bands":"UMTS 2100","notes":"holds license but not network built"},"29":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"29","brand":"aql","operator":"(aq) Limited","status":"Unknown","bands":"Unknown"},"70":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"70","operator":"AMSUK Ltd.","status":"Unknown","bands":"Unknown"},"71":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"71","operator":"Home Office","status":"Unknown","bands":"Unknown"},"72":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"72","operator":"Hanhaa Limited","status":"Operational","bands":"MVNO","notes":"M2M applications"},"30":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"30","brand":"T-Mobile UK","operator":"EE","status":"Operational","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600","notes":"Previously owned by Deutsche Telekom; used by MVNOs Asda Mobile & Virgin Mobile"},"31":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"31","brand":"T-Mobile UK","operator":"EE","status":"Allocated","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600"},"32":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"32","brand":"T-Mobile UK","operator":"EE","status":"Allocated","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600"},"76":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"76","brand":"BT","operator":"BT Group","status":"Operational","bands":"GSM 900 / GSM 1800"},"33":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"33","brand":"Orange","operator":"EE","status":"Operational","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600","notes":"Previously owned by Orange S.A."},"34":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"34","brand":"Orange","operator":"EE","status":"Operational","bands":"GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600","notes":"Previously owned by Orange S.A."},"78":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"78","brand":"Airwave","operator":"Airwave Solutions Ltd","status":"Operational","bands":"TETRA"},"35":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"35","operator":"JSC Ingenium (UK) Limited","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"36":{"type":"National","countryName":"Isle of Man (United Kingdom)","countryCode":"IM","mcc":"234","mnc":"36","brand":"Sure Mobile","operator":"Sure Isle of Man Ltd.","status":"Operational","bands":"GSM 900 / GSM 1800 / LTE","notes":"Former Cable & Wireless"},"37":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"37","operator":"Synectiv Ltd","status":"Unknown","bands":"Unknown"},"38":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"38","brand":"Virgin Mobile","operator":"Virgin Media","status":"Unknown","bands":"Unknown"},"39":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"39","operator":"Gamma Telecom Holdings Ltd.","status":"Unknown","bands":"Unknown","notes":"Former SSE Energy Supply Limited"},"86":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"234","mnc":"86","operator":"EE","status":"Unknown","bands":"Unknown"}},"356":{"110":{"type":"National","countryName":"Saint Kitts and Nevis","countryCode":"KN","mcc":"356","mnc":"110","brand":"FLOW","operator":"Cable & Wireless St. Kitts & Nevis Ltd","status":"Operational","bands":"GSM 850 / GSM 1900 / LTE 700"},"070":{"type":"National","countryName":"Saint Kitts and Nevis","countryCode":"KN","mcc":"356","mnc":"070","brand":"Chippie","operator":"UTS","status":"Operational"},"050":{"type":"National","countryName":"Saint Kitts and Nevis","countryCode":"KN","mcc":"356","mnc":"050","brand":"Digicel","operator":"Wireless Ventures (St Kitts-Nevis) Limited","status":"Operational","bands":"GSM 900 / GSM 1800"}},"235":{"00":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"00","brand":"Vectone Mobile","operator":"Mundio Mobile Limited","status":"Unknown"},"77":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"77","brand":"BT","operator":"BT Group","status":"Unknown"},"88":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"88","operator":"Telet Research (N.I.) Limited","status":"Unknown","bands":"LTE"},"01":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"01","operator":"EE","status":"Unknown","bands":"Unknown"},"02":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"02","operator":"EE","status":"Unknown","bands":"Unknown"},"03":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"03","brand":"Relish","operator":"UK Broadband Limited","status":"Unknown","bands":"Unknown"},"91":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"91","brand":"Vodafone UK","operator":"Vodafone United Kingdom","status":"Unknown"},"92":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"92","brand":"Vodafone UK","operator":"Vodafone United Kingdom","status":"Not operational","notes":"Former Cable & Wireless UK; MNC withdrawn"},"94":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"94","operator":"Hutchison 3G UK Ltd","status":"Unknown"},"95":{"type":"National","countryName":"United Kingdom","countryCode":"GB","mcc":"235","mnc":"95","operator":"Network Rail Infrastructure Limited","status":"Test Network","bands":"GSM-R"}},"358":{"110":{"type":"National","countryName":"Saint Lucia","countryCode":"LC","mcc":"358","mnc":"110","brand":"FLOW","operator":"Cable & Wireless","status":"Operational","bands":"GSM 850 / LTE 700"}},"238":{"66":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"66","operator":"TT-Netværket P/S","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former Telia, now shared network Telia/Telenor"},"01":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"01","brand":"TDC","operator":"TDC A/S","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"23":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"23","brand":"GSM-R DK","operator":"Banedanmark","status":"Operational","bands":"GSM-R"},"02":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"02","brand":"Telenor","operator":"Telenor Denmark","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former Sonofon"},"03":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"03","operator":"Syniverse Technologies","status":"Unknown","bands":"Unknown","notes":"Former End2End / MIGway A/S / MACH Connectivity"},"25":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"25","brand":"Viahub","operator":"SMS Provider Corp.","status":"Unknown","bands":"MVNO"},"04":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"04","operator":"NextGen Mobile Ltd T/A CardBoardFish","status":"Unknown","bands":"Unknown"},"05":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"05","brand":"TetraNet","operator":"Dansk Beredskabskommunikation A/S","status":"Operational","bands":"TETRA","notes":"Former ApS KBUS 38 nr. 4418; owned by Motorola Solutions"},"06":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"06","brand":"3","operator":"Hi3G Denmark ApS","status":"Operational","bands":"UMTS 900 / UMTS 2100 / LTE 1800 / LTE 2600"},"28":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"28","operator":"LINK Mobile A/S","status":"Unknown","bands":"Unknown","notes":"Former CoolTEL ApS"},"07":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"07","brand":"Vectone Mobile","operator":"Mundio Mobile (Denmark) Limited","status":"Operational","bands":"MVNO","notes":"Former Barablu MNO: Denmark Telenor"},"08":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"08","brand":"Voxbone","operator":"Voxbone mobile","status":"Operational","bands":"MVNO","notes":"Former Nordisk Mobiltelefon"},"09":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"09","brand":"SINE","operator":"Dansk Beredskabskommunikation A/S","status":"Operational","bands":"TETRA","notes":"Owned by Motorola Solutions"},"73":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"73","operator":"Onomondo ApS","status":"Unknown","bands":"Unknown"},"30":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"30","operator":"Interactive digital media GmbH","status":"Unknown","bands":"Unknown","notes":"Former Telia"},"10":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"10","brand":"TDC","operator":"TDC A/S","status":"Operational","bands":"Unknown","notes":"Test network"},"11":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"11","brand":"SINE","operator":"Dansk Beredskabskommunikation A/S","status":"Operational","bands":"TETRA","notes":"Test network"},"77":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"77","brand":"Telenor","operator":"Telenor Denmark","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Former Tele2"},"12":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"12","brand":"Lycamobile","operator":"Lycamobile Denmark Ltd","status":"Operational","bands":"MVNO"},"13":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"13","operator":"Compatel Limited","status":"Unknown","bands":"Unknown"},"14":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"14","operator":"Monty UK Global Limited","status":"Unknown","bands":"Unknown"},"15":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"15","operator":"Ice Danmark ApS","status":"Unknown","bands":"Unknown"},"16":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"16","operator":"Tismi B.V.","status":"Unknown","bands":"Unknown"},"17":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"17","operator":"Naka AG","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"18":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"18","operator":"Cubic Telecom","status":"Unknown","bands":"Unknown"},"40":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"40","operator":"Ericsson Danmark A/S","status":"Not operational","bands":"Unknown","notes":"Test network; former Sense Communications Denmark A/S; MNC withdrawn"},"20":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"20","brand":"Telia","operator":"Telia","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"42":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"42","operator":"Greenwave Mobile IoT ApS","status":"Unknown","bands":"Unknown","notes":"Former Brandtel ApS, Tel42 ApS"},"43":{"type":"National","countryName":"Denmark (Kingdom of Denmark)","countryCode":"DK","mcc":"238","mnc":"43","operator":"MobiWeb Limited","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"}},"360":{"110":{"type":"National","countryName":"Saint Vincent and the Grenadines","countryCode":"VC","mcc":"360","mnc":"110","brand":"FLOW","operator":"Cable & Wireless (St. Vincent & the Grenadines) Ltd","status":"Operational","bands":"GSM 850"},"100":{"type":"National","countryName":"Saint Vincent and the Grenadines","countryCode":"VC","mcc":"360","mnc":"100","brand":"Cingular Wireless","status":"Unknown","bands":"GSM 850"},"050":{"type":"National","countryName":"Saint Vincent and the Grenadines","countryCode":"VC","mcc":"360","mnc":"050","brand":"Digicel","operator":"Digicel (St. Vincent and the Grenadines) Limited","status":"Operational","bands":"GSM 900 / GSM 1800 / GSM 1900"}},"240":{"44":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"44","operator":"Telenabler AB","status":"Unknown","bands":"Unknown","notes":"Former Limitless Mobile AB"},"01":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"01","brand":"Telia","operator":"TeliaSonera Sverige AB","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / LTE 800 / LTE 1800 / LTE 2600"},"45":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"45","operator":"Spirius AB","status":"Unknown","bands":"Unknown"},"02":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"02","brand":"3","operator":"HI3G Access AB","status":"Operational","bands":"UMTS 900 / UMTS 2100 / LTE 800 / LTE 2600 / TD-LTE 2600"},"46":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"46","brand":"Viahub","operator":"SMS Provider Corp.","status":"Unknown","bands":"MVNO"},"03":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"03","brand":"Net 1","operator":"Netett Sverige AB","status":"Operational","bands":"LTE 450","notes":"Former Ice.net; CDMA 450 shut down"},"47":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"47","operator":"Viatel Sweden AB","status":"Unknown","bands":"Unknown"},"04":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"04","brand":"SWEDEN","operator":"3G Infrastructure Services AB","status":"Operational","bands":"UMTS 2100","notes":"Owned by Hi3G Access (3) and Telenor. Not available in major cities since the owners operate their own city networks."},"05":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"05","brand":"Sweden 3G","operator":"Svenska UMTS-Nät AB","status":"Operational","bands":"UMTS 2100","notes":"Owned by Telia and Tele2. Available all over Sweden."},"06":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"06","brand":"Telenor","operator":"Telenor Sverige AB","status":"Operational","bands":"UMTS 2100","notes":"former Vodafone Sweden"},"07":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"07","brand":"Tele2","operator":"Tele2 Sverige AB","status":"Operational","bands":"UMTS 2100 / LTE 800 / LTE 900 / LTE 1800 / LTE 2600","notes":"MOCN r6 network"},"08":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"08","brand":"Telenor","operator":"Telenor Sverige AB","status":"Not operational","bands":"GSM 900 / GSM 1800","notes":"Now merged with Tele2 into Net4Mobility"},"09":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"09","brand":"Com4","operator":"Communication for Devices in Sweden AB","status":"Unknown","bands":"Unknown","notes":"former djuice (Telenor MVNO)"},"10":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"10","brand":"Spring Mobil","operator":"Tele2 Sverige AB","status":"Operational","notes":"Only used on femto- and nanocells"},"11":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"11","operator":"ComHem AB","status":"Unknown","bands":"Unknown","notes":"Former Lindholmen Science Park AB"},"12":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"12","brand":"Lycamobile","operator":"Lycamobile Sweden Limited","status":"Operational","bands":"MVNO"},"13":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"13","operator":"Alltele Företag Sverige AB","status":"Unknown","bands":"Unknown"},"14":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"14","operator":"Tele2 Business AB","status":"Unknown","bands":"Unknown","notes":"Former TDC Sverige AB (MVNO)"},"15":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"15","operator":"Wireless Maingate Nordic AB","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100"},"16":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"16","operator":"42 Telecom AB","status":"Operational","bands":"GSM"},"17":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"17","brand":"Gotanet","operator":"Götalandsnätet AB","status":"Operational","bands":"MVNO"},"18":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"18","operator":"Generic Mobile Systems Sweden AB","status":"Unknown","bands":"Unknown"},"19":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"19","brand":"Vectone Mobile","operator":"Mundio Mobile (Sweden) Limited","status":"Operational","bands":"MVNO","notes":"MVNO in Telia's network"},"60":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"60","operator":"Telefonaktiebolaget LM Ericsson","status":"Unknown","bands":"Unknown","notes":"Test network; Temporary license until 31 December 2018"},"61":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"61","operator":"MessageBird B.V.","status":"Unknown","bands":"Unknown"},"20":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"20","operator":"Wireless Maingate Messaging Services AB","status":"Operational","bands":"GSM"},"21":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"21","brand":"MobiSir","operator":"Trafikverket ICT","status":"Operational","bands":"GSM-R 900"},"22":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"22","operator":"EuTel AB","status":"Unknown","bands":"Unknown"},"23":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"23","operator":"Infobip Limited (UK)","status":"Not operational","bands":"Unknown"},"24":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"24","brand":"Sweden 2G","operator":"Net4Mobility HB","status":"Operational","bands":"GSM 900 / LTE 800 / LTE 900 / LTE 1800 / LTE 2600","notes":"LTE1800 only available in major cities, it was deployed mostly to boost sales of the iPhone 5; owned by Telenor and Tele2."},"25":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"25","operator":"Monty UK Global Ltd","status":"Unknown","bands":"Unknown","notes":"Former Digitel Mobile Srl"},"26":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"26","operator":"Twilio Sweden AB","status":"Unknown","bands":"Unknown","notes":"Former Beepsend AB"},"27":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"27","operator":"GlobeTouch AB","status":"Operational","bands":"MVNO","notes":"Former Fogg Mobile AB; M2M services only"},"28":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"28","operator":"LINK Mobile A/S","status":"Unknown","bands":"Unknown","notes":"Former CoolTEL Aps"},"29":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"29","operator":"Mercury International Carrier Services","status":"Unknown","bands":"Unknown"},"30":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"30","operator":"NextGen Mobile Ltd.","status":"Unknown","bands":"Unknown"},"31":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"31","operator":"RebTel Network AB","status":"Unknown","bands":"Unknown","notes":"Former Mobimax AB"},"32":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"32","operator":"Compatel Limited","status":"Unknown","bands":"Unknown"},"33":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"33","operator":"Mobile Arts AB","status":"Unknown","bands":"Unknown"},"34":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"34","operator":"Pro Net Telecommunications Services Ltd.","status":"Not operational","bands":"Unknown","notes":"Formerly Tigo; MNC withdrawn"},"35":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"35","operator":"42 Telecom LTD","status":"Unknown","bands":"Unknown"},"36":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"36","operator":"interactive digital media GmbH","status":"Unknown","bands":"Unknown"},"37":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"37","operator":"CLX Networks AB","status":"Operational","bands":"Unknown"},"38":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"38","brand":"Voxbone","operator":"Voxbone mobile","status":"Operational","bands":"MVNO"},"39":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"39","operator":"Borderlight AB","status":"Unknown","bands":"Unknown","notes":"Former iCentrex Sweden AB"},"40":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"40","operator":"North net connect AB","status":"Unknown","bands":"Unknown","notes":"Former ReWiCom Scandinavia AB"},"41":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"41","operator":"Shyam Telecom UK Ltd.","status":"Unknown","bands":"Unknown"},"42":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"42","operator":"Telenor Connexion AB","status":"Unknown","bands":"Unknown"},"43":{"type":"National","countryName":"Sweden","countryCode":"SE","mcc":"240","mnc":"43","operator":"MobiWeb Ltd.","status":"Unknown","bands":"Unknown"}},"362":{"33":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"33","operator":"WICC N.V.","status":"Unknown","bands":"GSM"},"78":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"78","brand":"Telbo","operator":"Telefonia Bonairiano N.V.","status":"Operational","bands":"UMTS 900 / LTE 1800","notes":"Bonaire"},"68":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"68","brand":"Digicel","operator":"Curaçao Telecom N.V.","status":"Operational","bands":"UMTS 2100 / LTE 1800","notes":"Curaçao"},"69":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"69","brand":"Digicel","operator":"Curaçao Telecom N.V.","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Curaçao"},"59":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"59","brand":"Chippie","operator":"United Telecommunication Service N.V. (UTS)","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Bonaire, Saba, Sint Eustatius, Sint Maarten; former Radcomm N.V."},"91":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"91","brand":"Chippie","operator":"United Telecommunication Service N.V. (UTS)","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 850 / UMTS 2100 / LTE 1800","notes":"Curaçao; former Setel N.V."},"60":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"60","brand":"Chippie","operator":"United Telecommunication Service N.V. (UTS)","status":"Operational","bands":"UMTS 2100 / LTE 1800","notes":"Bonaire, Saba, Sint Eustatius, Sint Maarten; former Radcomm N.V."},"94":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"94","brand":"Bayòs","operator":"Bòbò Frus N.V.","status":"Operational","bands":"TDMA PCS","notes":"Mobile Solutions"},"51":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"51","brand":"Telcell","operator":"Telcell N.V.","status":"Operational","bands":"GSM 900 / UMTS 2100 / LTE 1800","notes":"Sint Maarten"},"95":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"95","brand":"MIO","operator":"E.O.C.G. Wireless","status":"Not operational","bands":"CDMA2000 850","notes":"former GSM Caribbean N.V.; bankrupt in 2013"},"63":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"63","operator":"CSC N.V.","status":"Unknown","bands":"Unknown"},"74":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"74","operator":"PCS N.V.","status":"Unknown","bands":"Unknown"},"31":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"31","operator":"Eutel N.V.","status":"Unknown","bands":"GSM","notes":"Sint Eustatius"},"54":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"54","brand":"ECC","operator":"East Caribbean Cellular","status":"Operational","bands":"GSM 900 / GSM 1800"},"76":{"type":"National","countryName":"Former Netherlands Antilles (Kingdom of the Netherlands)","countryCode":"BQ/CW/SX","mcc":"362","mnc":"76","brand":"Digicel","operator":"Antiliano Por N.V.","status":"Operational","bands":"GSM 900 / UMTS","notes":"Bonaire"}},"363":{"01":{"type":"National","countryName":"Aruba (Kingdom of the Netherlands)","countryCode":"AW","mcc":"363","mnc":"01","brand":"SETAR","operator":"Servicio di Telecomunicacion di Aruba","status":"Operational","bands":"GSM 900 / GSM 1800 / GSM 1900 / UMTS 2100 / LTE 1800 / TDMA 800"},"02":{"type":"National","countryName":"Aruba (Kingdom of the Netherlands)","countryCode":"AW","mcc":"363","mnc":"02","brand":"Digicel","operator":"Digicel Aruba","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100"}},"242":{"11":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"11","brand":"SystemNet","operator":"SystemNet AS","status":"Unknown","bands":"Test"},"22":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"22","operator":"Altibox AS","status":"Unknown","bands":"Unknown","notes":"Former Network Norway AS"},"99":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"99","operator":"TampNet AS","status":"Operational","bands":"LTE","notes":"Offshore"},"01":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"01","brand":"Telenor","operator":"Telenor Norge AS","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"12":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"12","brand":"Telenor","operator":"Telenor Norge AS","status":"Unknown","bands":"Unknown"},"23":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"23","brand":"Lycamobile","operator":"Lyca Mobile Ltd","status":"Operational","bands":"MVNO"},"02":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"02","brand":"Telia","operator":"TeliaSonera Norge AS","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former NetCom"},"24":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"24","operator":"Mobile Norway AS","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"03":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"03","operator":"Televerket AS","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"14":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"14","brand":"ICE","operator":"ICE Communication Norge AS","status":"Operational","bands":"GSM 900 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800"},"25":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"25","operator":"Forsvarets kompetansesenter KKIS","status":"Unknown","bands":"Unknown"},"04":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"04","brand":"Tele2","operator":"Tele2 (Mobile Norway AS)","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"05":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"05","brand":"Telia","operator":"TeliaSonera Norge AS","status":"Not operational","bands":"GSM 900 / UMTS 900 / UMTS 2100","notes":"Former Tele2"},"06":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"06","brand":"ICE","operator":"ICE Norge AS","status":"Operational","bands":"LTE 450","notes":"Former Nordisk Mobiltelefon; data services only"},"07":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"07","brand":"Phonero","operator":"Phonero AS","status":"Not operational","bands":"MVNO","notes":"Former Ventelo; MNC withdrawn"},"08":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"08","brand":"TDC","operator":"TDC Mobil AS","status":"Operational","bands":"MVNO"},"09":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"09","brand":"Com4","operator":"Com4 AS","status":"Operational","bands":"MVNO","notes":"Principally M2M services"},"90":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"90","operator":"Nokia Solutions and Networks Norge AS","status":"Unknown","bands":"Unknown"},"20":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"20","operator":"Jernbaneverket AS","status":"Operational","bands":"GSM-R 900"},"10":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"10","operator":"Norwegian Communications Authority","status":"Unknown","bands":"Unknown"},"21":{"type":"National","countryName":"Norway","countryCode":"NO","mcc":"242","mnc":"21","operator":"Jernbaneverket AS","status":"Operational","bands":"GSM-R 900"}},"001":{"01":{"type":"Test","mcc":"001","mnc":"01","brand":"TEST","operator":"Test Network","status":"Operational","bands":"GSM 900"}},"364":{"49":{"type":"National","countryName":"Bahamas","countryCode":"BS","mcc":"364","mnc":"49","brand":"Aliv","operator":"Cable Bahamas Ltd","status":"Operational","bands":"LTE 700 / LTE AWS","notes":"Former NewCo 2015; LTE bands 13 / 4, license also covers 850MHz and 1900MHz"},"39":{"type":"National","countryName":"Bahamas","countryCode":"BS","mcc":"364","mnc":"39","brand":"BTC","operator":"The Bahamas Telecommunications Company Ltd (BaTelCo)","status":"Operational","bands":"GSM 850 / GSM 1900 / UMTS 850 / LTE 700","notes":"LTE band 17"}},"365":{"840":{"type":"National","countryName":"Anguilla (United Kingdom)","countryCode":"AI","mcc":"365","mnc":"840","brand":"FLOW","operator":"Cable & Wireless","status":"Operational","bands":"GSM 850 / UMTS / LTE 700"},"010":{"type":"National","countryName":"Anguilla (United Kingdom)","countryCode":"AI","mcc":"365","mnc":"010","operator":"Weblinks Limited","status":"Operational","bands":"Unknown"}},"244":{"22":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"22","operator":"EXFO Oy","status":"Not operational","bands":"Unknown","notes":"Former NetHawk Oyj; MNC withdrawn"},"44":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"44","operator":"Turun ammattikorkeakoulu Oy","status":"Unknown","bands":"Unknown"},"23":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"23","operator":"EXFO Oy","status":"Not operational","bands":"Unknown","notes":"Former NetHawk Oyj; MNC withdrawn"},"24":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"24","operator":"TTY-säätiö","status":"Not operational","bands":"Unknown","notes":"Tampere University of Technology foundation; MNC withdrawn"},"03":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"03","brand":"DNA","operator":"DNA Oy","status":"Operational","bands":"GSM 1800","notes":"Former Telia"},"25":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"25","brand":"Datame","operator":"Datame Oy","status":"Not operational","bands":"CDMA","notes":"MNC withdrawn"},"04":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"04","brand":"DNA","operator":"DNA Oy","status":"Unknown","bands":"Unknown","notes":"Former Aina Oyj"},"26":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"26","brand":"Compatel","operator":"Compatel Ltd","status":"Operational","bands":"MVNO"},"05":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"05","brand":"Elisa","operator":"Elisa Oyj","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former Radiolinja"},"27":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"27","operator":"Teknologian tutkimuskeskus VTT Oy","status":"Unknown","bands":"Unknown","notes":"VTT Technical Research Centre of Finland"},"06":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"06","brand":"Elisa","operator":"Elisa Oyj","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"28":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"28","operator":"Teknologian tutkimuskeskus VTT Oy","status":"Unknown","bands":"Unknown","notes":"VTT Technical Research Centre of Finland"},"07":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"07","brand":"Nokia","operator":"Nokia Solutions and Networks Oy","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800 / LTE 2600 / TD-LTE 2600","notes":"Test network in Espoo Leppävaara and Nokia HQ"},"29":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"29","operator":"SCNL Truphone","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"08":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"08","brand":"Nokia","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"GSM 1800 / UMTS 2100"},"09":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"09","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"GSM 900","notes":"Former Finnet Group"},"91":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"91","brand":"Sonera","operator":"TeliaSonera Finland Oyj","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 700 / LTE 800 / LTE 1800 / LTE 2600"},"92":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"92","brand":"Sonera","operator":"TeliaSonera Finland Oyj","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"30":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"30","brand":"Vectone Mobile","operator":"Mundio Mobile Oy","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"31":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"31","brand":"Kuiri","operator":"Ukko Mobile Oy","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"10":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"10","operator":"Viestintävirasto","status":"Unknown","bands":"Unknown","notes":"Former TDC Oy Finland"},"32":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"32","brand":"Voxbone","operator":"Voxbone SA","status":"Operational","bands":"MVNO"},"11":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"11","operator":"Viestintävirasto","status":"Unknown","bands":"Unknown","notes":"Former Vectone Mobile"},"33":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"33","brand":"VIRVE","operator":"Virve Tuotteet ja Palvelut Oy","status":"Operational","bands":"TETRA","notes":"Finnish authorities radio network"},"12":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"12","brand":"DNA","operator":"DNA Oy","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"34":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"34","brand":"Bittium Wireless","operator":"Bittium Wireless Oy","status":"Operational","bands":"MVNO"},"13":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"13","brand":"DNA","operator":"DNA Oy","status":"Not operational","bands":"GSM 900 / GSM 1800"},"35":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"35","brand":"Ukko Mobile","operator":"Ukkoverkot Oy","status":"Operational","bands":"LTE 450 / TD-LTE 2600","notes":"data-only network"},"14":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"14","brand":"Ålcom","operator":"Ålands Telekommunikation Ab","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800","notes":"Former Ålands Mobiltelefon (ÅMT); coverage only in Åland Islands"},"36":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"36","brand":"Sonera / DNA","operator":"TeliaSonera Finland Oyj / Suomen Yhteisverkko Oy","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Joint mobile network in Northern and Eastern Finland areas"},"15":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"15","brand":"SAMK","operator":"Satakunnan ammattikorkeakoulu Oy","status":"Not operational","bands":"GSM 1800","notes":"Educational network of Satakunta University of Applied Sciences; MNC withdrawn"},"37":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"37","brand":"Tismi","operator":"Tismi BV","status":"Operational","bands":"MVNO"},"16":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"16","brand":"Tele2","operator":"Oy Finland Tele2 AB","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"38":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"38","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"Unknown","notes":"Test Network"},"17":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"17","operator":"Liikennevirasto","status":"Operational","bands":"GSM-R","notes":"Finnish Transport Agency"},"39":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"39","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"Unknown","notes":"Test Network"},"40":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"40","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"Unknown","notes":"Test Network"},"41":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"41","operator":"Nokia Solutions and Networks Oy","status":"Unknown","bands":"Unknown","notes":"Test Network"},"42":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"42","operator":"SMS Provider Corp.","status":"Unknown","bands":"Unknown"},"21":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"21","brand":"Elisa- Saunalahti","operator":"Elisa Oyj","status":"Operational","bands":"MVNO","notes":"Internal MVNO-code of Elisa Oyj. Former Saunalahti Group Oyj"},"43":{"type":"National","countryName":"Finland","countryCode":"FI","mcc":"244","mnc":"43","operator":"Telavox AB / Telavox Oy","status":"Unknown","bands":"Unknown"}},"366":{"110":{"type":"National","countryName":"Dominica","countryCode":"DM","mcc":"366","mnc":"110","brand":"FLOW","operator":"Cable & Wireless","status":"Operational","bands":"GSM 850 / UMTS / LTE 700"},"020":{"type":"National","countryName":"Dominica","countryCode":"DM","mcc":"366","mnc":"020","brand":"Digicel","operator":"Digicel Group Limited","status":"Operational","bands":"GSM 900 / GSM 1900 / UMTS 900 / UMTS 1800 / UMTS 1900 / LTE","notes":"Former Orange Dominica"}},"246":{"01":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"01","brand":"Telia","operator":"Telia Lietuva","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800","notes":"Former Omnitel"},"02":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"02","brand":"BITĖ","operator":"UAB Bitė Lietuva","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"03":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"03","brand":"Tele2","operator":"UAB Tele2 (Tele2 AB, Sweden)","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"(in Vodafone partnership)"},"04":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"04","operator":"LR vidaus reikalų ministerija (Ministry of the Interior)","status":"Unknown","bands":"Unknown"},"05":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"05","brand":"LitRail","operator":"Lietuvos geležinkeliai (Lithuanian Railways)","status":"Operational","bands":"GSM-R 900"},"06":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"06","brand":"Mediafon","operator":"UAB Mediafon","status":"Operational","bands":"Unknown"},"07":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"07","operator":"Compatel Ltd.","status":"Unknown","bands":"Unknown"},"08":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"08","brand":"MEZON","operator":"Lietuvos radijo ir televizijos centras","status":"Operational","bands":"WiMAX 3500 / TD-LTE 2300"},"09":{"type":"National","countryName":"Lithuania","countryCode":"LT","mcc":"246","mnc":"09","operator":"Interactive Digital Media GmbH","status":"Unknown","bands":"Unknown"}},"368":{"01":{"type":"National","countryName":"Cuba","countryCode":"CU","mcc":"368","mnc":"01","brand":"CUBACEL","operator":"Empresa de Telecomunicaciones de Cuba, SA","status":"Operational","bands":"GSM 900 / GSM 850 / UMTS 900","notes":"GSM 850 only available in limited areas (Havana, Varadero, Trinidad and Cayo Coco)"}},"247":{"01":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"01","brand":"LMT","operator":"Latvian Mobile Telephone","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 1800 / LTE 2600"},"02":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"02","brand":"Tele2","operator":"Tele2","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"03":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"03","brand":"TRIATEL","operator":"Telekom Baltija","status":"Operational","bands":"CDMA 450"},"04":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"04","operator":"Beta Telecom","status":"Not operational","bands":"Unknown","notes":"Former Lattelecom; MNC withdrawn"},"05":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"05","brand":"Bite","operator":"Bite Latvija","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Bite's postpaid customers are still being assigned SIM cards with 246 02 MNC"},"06":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"06","operator":"Rigatta","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"07":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"07","operator":"SIA \"MEGATEL\"","status":"Operational","bands":"MVNO","notes":"Uses Bite network; former Master Telecom"},"08":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"08","brand":"IZZI","operator":"IZZI","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"09":{"type":"National","countryName":"Latvia","countryCode":"LV","mcc":"247","mnc":"09","brand":"Xomobile","operator":"Camel Mobile","status":"Operational","bands":"MVNO","notes":"Former Global Mobile Solutions"}},"248":{"11":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"11","operator":"UAB Raystorm Eesti filiaal","status":"Unknown","bands":"Unknown"},"01":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"01","brand":"Telia","operator":"Estonian Mobile Telecom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former EMT"},"02":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"02","brand":"Elisa","operator":"Elisa Eesti","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"03":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"03","brand":"Tele2","operator":"Tele2 Eesti","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600"},"04":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"04","brand":"Top Connect","operator":"OY Top Connect","status":"Operational","bands":"MVNO"},"05":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"05","operator":"AS Bravocom Mobiil","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"06":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"06","operator":"Progroup Holding","status":"Not operational","bands":"UMTS 2100","notes":"MNC withdrawn"},"07":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"07","brand":"Kou","operator":"Televõrgu AS","status":"Not operational","bands":"CDMA2000 450","notes":"Acquired by Tele 2 in 2012; shut down in January 2016"},"08":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"08","brand":"VIVEX","operator":"VIVEX OU","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn"},"09":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"09","operator":"Bravo Telecom","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"71":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"71","operator":"Siseministeerium (Ministry of Interior)","status":"Unknown","bands":"Unknown"},"10":{"type":"National","countryName":"Estonia","countryCode":"EE","mcc":"248","mnc":"10","operator":"Telcotrade OÜ","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"}},"370":{"01":{"type":"National","countryName":"Dominican Republic","countryCode":"DO","mcc":"370","mnc":"01","brand":"Altice","operator":"Altice Group","status":"Operational","bands":"GSM 900 / GSM 1800 / GSM 1900 / UMTS 900 / LTE 1800","notes":"Former Orange Dominicana"},"02":{"type":"National","countryName":"Dominican Republic","countryCode":"DO","mcc":"370","mnc":"02","brand":"Claro","operator":"Compañía Dominicana de Teléfonos","status":"Operational","bands":"GSM 850 / GSM 1900 / UMTS 850 / LTE 1700","notes":"CDMA 1900 shut down in 2014"},"03":{"type":"National","countryName":"Dominican Republic","countryCode":"DO","mcc":"370","mnc":"03","brand":"Altice","operator":"Altice Group","status":"Operational","bands":"AMPS / CDMA 850","notes":"Former Tricom, S.A, 1900MHz spectrum returned to regulator"},"04":{"type":"National","countryName":"Dominican Republic","countryCode":"DO","mcc":"370","mnc":"04","brand":"Viva","operator":"Trilogy Dominicana, S.A.","status":"Operational","bands":"CDMA 1900 / GSM 1900","notes":"Former Centennial Dominicana"},"05":{"type":"National","countryName":"Dominican Republic","countryCode":"DO","mcc":"370","mnc":"05","brand":"Wind","operator":"WIND Telecom, S.A","status":"Operational","bands":"TD-LTE 2600","notes":"LTE band 38"}},"250":{"22":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"22","operator":"Vainakh Telecom","status":"Operational","bands":"TD-LTE 2300"},"44":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"44","operator":"Stavtelesot / North Caucasian GSM","status":"Not operational","bands":"Unknown"},"01":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"01","brand":"MTS","operator":"Mobile TeleSystems","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600 / TD-LTE 2600"},"23":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"23","brand":"Thuraya","operator":"GTNT","status":"Operational","bands":"Satellite MVNO","notes":"Former Mobicom Novosibirsk"},"02":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"02","brand":"MegaFon","operator":"MegaFon PJSC","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former North-West GSM"},"03":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"03","brand":"NCC","operator":"Nizhegorodskaya Cellular Communications","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Purchased by Tele2"},"04":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"04","brand":"Sibchallenge","operator":"Sibchallenge","status":"Not operational","bands":"GSM 900"},"05":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"05","brand":"ETK","operator":"Yeniseytelecom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / CDMA2000 450","notes":"Mobile Communications Systems"},"06":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"06","brand":"Skylink","operator":"CJSC Saratov System of Cellular Communications","status":"Operational","bands":"CDMA2000 450"},"28":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"28","brand":"Beeline","operator":"Beeline","status":"Not operational","bands":"GSM 900","notes":"Former EXTEL"},"07":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"07","brand":"SMARTS","operator":"Zao SMARTS","status":"Operational","bands":"GSM 900 / GSM 1800"},"29":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"29","brand":"Iridium","operator":"Iridium Communications","status":"Operational","bands":"Satellite MVNO"},"08":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"08","brand":"Vainah Telecom","operator":"CS \"VainahTelecom\"","status":"Operational","bands":"GSM 900 / GSM 1800 / LTE 2300"},"09":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"09","brand":"Skylink","operator":"Khabarovsky Cellular Phone","status":"Operational","bands":"CDMA2000 450"},"91":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"91","brand":"Sonic Duo","operator":"Sonic Duo CJSC","status":"Not operational","bands":"GSM 1800"},"811":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"811","operator":"Votek Mobile","status":"Not operational","bands":"AMPS / DAMPS / GSM 1800"},"92":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"92","operator":"Primtelefon","status":"Not operational","bands":"Unknown"},"93":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"93","operator":"Telecom XXI","status":"Not operational","bands":"Unknown"},"50":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"50","brand":"MTS","operator":"Bezlimitno.ru","status":"Operational","bands":"MVNO","notes":"Based on MTS"},"10":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"10","brand":"DTC","operator":"Dontelekom","status":"Not operational","bands":"GSM 900"},"32":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"32","brand":"Win Mobile","operator":"K-Telecom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800","notes":"Operational in Crimea only."},"54":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"54","brand":"TTK","operator":"Tattelecom","status":"Operational","bands":"LTE 1800"},"11":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"11","brand":"Yota","operator":"Scartel","status":"Operational","bands":"MVNO"},"33":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"33","brand":"Sevmobile","operator":"Sevtelekom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"Operational in Sevastopol only."},"99":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"99","brand":"Beeline","operator":"OJSC Vimpel-Communications","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600"},"12":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"12","brand":"Baykalwestcom","operator":"Baykal Westcom / New Telephone Company / Far Eastern Cellular","status":"Operational","bands":"GSM 900 / GSM 1800 / CDMA2000 450"},"34":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"34","brand":"Krymtelekom","operator":"Krymtelekom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"Operational in Crimea only."},"13":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"13","brand":"KUGSM","operator":"Kuban GSM","status":"Not operational","bands":"GSM 900 / GSM 1800"},"35":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"35","brand":"MOTIV","operator":"EKATERINBURG-2000","status":"Operational","bands":"GSM 1800 / LTE 1800"},"14":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"14","brand":"MegaFon","operator":"MegaFon OJSC","status":"Not operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / TD-LTE 2600"},"15":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"15","brand":"SMARTS","operator":"SMARTS Ufa, SMARTS Uljanovsk","status":"Operational","bands":"GSM 1800"},"16":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"16","brand":"NTC","operator":"New Telephone Company","status":"Operational","bands":"GSM 900 / GSM 1800"},"38":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"38","brand":"Tambov GSM","operator":"Central Telecommunication Company","status":"Operational","bands":"GSM 900 / GSM 1800"},"17":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"17","brand":"Utel","operator":"JSC Uralsvyazinform","status":"Operational","bands":"GSM 900 / GSM 1800","notes":"Former Ermak RMS"},"39":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"39","brand":"Rostelecom","operator":"ROSTELECOM","status":"Not operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / TD-LTE 2300 / LTE 2600","notes":"Tele2 code 250 20 is used since acquiring"},"18":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"18","brand":"Osnova Telecom","status":"Not operational","bands":"TD-LTE 2300"},"19":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"19","brand":"INDIGO","operator":"INDIGO","status":"Not operational","bands":"GSM 1800","notes":"Since 19 December 2009 merged with Tele2"},"60":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"60","brand":"Volna mobile","operator":"KTK Telecom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800","notes":"Operational in Crimea only."},"62":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"62","brand":"Tinkoff Mobile","operator":"Tinkoff Mobile","status":"Operational","bands":"MVNO"},"20":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"20","brand":"Tele2","operator":"Tele2","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 450 / LTE 1800 / LTE 2600"},"21":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"21","brand":"GlobalTel","operator":"JSC \"GlobalTel\"","status":"Operational","bands":"Satellite"},"?":{"type":"National","countryName":"Russian Federation","countryCode":"RU","mcc":"250","mnc":"?","brand":"SkyLink","operator":"SkyLink/MTS/the Moscow Cellular communication","status":"Operational","bands":"CDMA2000 450"}},"372":{"01":{"type":"National","countryName":"Haiti","countryCode":"HT","mcc":"372","mnc":"01","brand":"Voila","operator":"Communication Cellulaire d'Haiti S.A.","status":"Not operational","bands":"GSM 850","notes":"Sold to Digicel in 2012"},"02":{"type":"National","countryName":"Haiti","countryCode":"HT","mcc":"372","mnc":"02","brand":"Digicel","operator":"Unigestion Holding S.A.","status":"Operational","bands":"GSM 1800"},"03":{"type":"National","countryName":"Haiti","countryCode":"HT","mcc":"372","mnc":"03","brand":"Natcom","operator":"NATCOM S.A.","status":"Operational","bands":"GSM 900 / GSM 1800 / UTMS 2100 / LTE","notes":"60% owned by Viettel"}},"374":{"12":{"type":"National","countryName":"Trinidad and Tobago","countryCode":"TT","mcc":"374","mnc":"12","brand":"bmobile","operator":"TSTT","status":"Operational","bands":"GSM 850 / GSM 1900 / UMTS 1900 / LTE 1900 / TD-LTE 2600"},"140":{"type":"National","countryName":"Trinidad and Tobago","countryCode":"TT","mcc":"374","mnc":"140","operator":"LaqTel Ltd.","status":"Not operational","bands":"CDMA","notes":"Shut down 2008"},"130":{"type":"National","countryName":"Trinidad and Tobago","countryCode":"TT","mcc":"374","mnc":"130","brand":"Digicel","operator":"Digicel (Trinidad & Tobago) Limited","status":"Operational","bands":"GSM 850 / GSM 1900 / UMTS 1900"}},"376":{"352":{"type":"National","countryName":"Turks and Caicos Islands","countryCode":"TC","mcc":"376","mnc":"352","brand":"FLOW","operator":"Cable & Wireless West Indies Ltd (Turks & Caicos)","status":"Operational","bands":"UMTS 850","notes":"Former IslandCom"},"360":{"type":"National","countryName":"Turks and Caicos Islands","countryCode":"TC","mcc":"376","mnc":"360","brand":"FLOW","operator":"Cable & Wireless West Indies Ltd (Turks & Caicos)","status":"Unknown","bands":"Unknown","notes":"Former IslandCom"},"350":{"type":"National","countryName":"Turks and Caicos Islands","countryCode":"TC","mcc":"376","mnc":"350","brand":"FLOW","operator":"Cable & Wireless West Indies Ltd (Turks & Caicos)","status":"Operational","bands":"GSM 850 / LTE 700"}},"255":{"01":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"01","brand":"Vodafone","operator":"PRJSC VF Ukraine","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 2600","notes":"Former UMC, MTS; CDMA 450 shut down June 2018"},"23":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"23","brand":"CDMA Ukraine","operator":"Intertelecom","status":"Not operational","bands":"CDMA 800","notes":"Taken over by Intertelecom"},"02":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"02","brand":"Beeline","operator":"Kyivstar GSM JSC","status":"Not operational","bands":"GSM 900 / GSM 1800","notes":"Former WellCOM, URS; taken over by Kyivstar"},"03":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"03","brand":"Kyivstar","operator":"Kyivstar JSC","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 2600"},"25":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"25","brand":"NEWTONE","operator":"CST Invest","status":"Operational","bands":"CDMA 800"},"04":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"04","brand":"IT","operator":"Intertelecom LLC","status":"Operational","bands":"CDMA 800"},"05":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"05","brand":"Golden Telecom","operator":"Kyivstar GSM JSC","status":"Not operational","bands":"GSM 1800","notes":"MNC withdrawn"},"06":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"06","brand":"lifecell","operator":"Turkcell","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 2600","notes":"Former life:) / Astelit"},"07":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"07","brand":"3Mob","operator":"Trymob LLC","status":"Operational","bands":"UMTS 2100","notes":"Former Utel, GSM roaming with MTS"},"21":{"type":"National","countryName":"Ukraine","countryCode":"UA","mcc":"255","mnc":"21","brand":"PEOPLEnet","operator":"Telesystems of Ukraine","status":"Operational","bands":"CDMA 800"}},"257":{"01":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"01","brand":"velcom","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100"},"02":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"02","brand":"MTS","operator":"Mobile TeleSystems","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100","notes":"LTE via beCloud"},"03":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"03","brand":"DIALLOG","operator":"BelCel","status":"Not operational","bands":"CDMA 450","notes":"Closed on 21 January 2014"},"04":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"04","brand":"life:)","operator":"Belarusian Telecommunications Network","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"Former BeST; LTE via beCloud"},"05":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"05","brand":"byfly","operator":"Beltelecom","status":"Not operational","bands":"WiMAX 3500","notes":"Closed on 01 May 2017"},"06":{"type":"National","countryName":"Belarus","countryCode":"BY","mcc":"257","mnc":"06","brand":"beCloud","operator":"Belorussian Cloud Technologies","status":"Operational","bands":"LTE 1800 / LTE 2600","notes":"Former Yota Bel; wholesale network used by MTS and life:)"}},"259":{"99":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"99","brand":"Unité","operator":"Moldtelecom","status":"Operational","bands":"UMTS 2100","notes":"Used for Femtocell service only"},"01":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"01","brand":"Orange","operator":"Orange Moldova","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former Voxtel"},"02":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"02","brand":"Moldcell","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 1800 / LTE 2600"},"03":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"03","brand":"IDC","operator":"Interdnestrcom","status":"Operational","bands":"CDMA 450 / CDMA 800","notes":"Sharing the same MNC with Unité"},"04":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"04","brand":"Eventis","operator":"Eventis Telecom","status":"Not operational","bands":"GSM 900 / GSM 1800","notes":"Bankruptcy - License suspended"},"15":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"15","brand":"IDC","operator":"Interdnestrcom","status":"Operational","bands":"LTE 800"},"05":{"type":"National","countryName":"Moldova","countryCode":"MD","mcc":"259","mnc":"05","brand":"Unité","operator":"Moldtelecom","status":"Operational","bands":"UMTS 900 / UMTS 2100 / LTE 1800"}},"260":{"44":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"44","operator":"Rebtel Poland Sp. z o.o.","status":"Unknown","bands":"Unknown"},"01":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"01","brand":"Plus","operator":"Polkomtel Sp. z o.o.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 900 / UMTS 2100 / LTE 1800 / LTE 2600","notes":"LTE roaming with Aero 2"},"45":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"45","operator":"Virgin Mobile Polska Sp. z o.o.","status":"Operational","bands":"MVNO"},"02":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"02","brand":"T-Mobile","operator":"T-Mobile Polska S.A.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"former Era; see MNC 260-34 for shared LTE network"},"46":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"46","operator":"Terra Telekom Sp. z o.o.","status":"Unknown","bands":"Unknown"},"03":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"03","brand":"Orange","operator":"Polska Telefonia Komórkowa Centertel Sp. z o.o.","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100","notes":"former Idea; see MNC 260-34 for shared LTE network; CDMA2000 450 shut down April 2017"},"47":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"47","operator":"SMShighway Limited","status":"Unknown","bands":"Unknown"},"04":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"04","brand":"Aero2","operator":"Aero 2 Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"former CenterNet S.A."},"48":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"48","operator":"AGILE TELECOM S.P.A.","status":"Unknown","bands":"Unknown"},"05":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"05","brand":"Orange","operator":"Polska Telefonia Komórkowa Centertel Sp. z o.o.","status":"Not operational","bands":"UMTS 2100","notes":"not in use, using MNC 03"},"49":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"49","operator":"Messagebird B.V.","status":"Unknown","bands":"Unknown"},"06":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"06","brand":"Play","operator":"P4 Sp. z o.o.","status":"Operational","bands":"GSM 900 / UMTS 900 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2100 / LTE 2600","notes":"Also roaming on Polkomtel and Orange 2G/3G network"},"07":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"07","brand":"Netia","operator":"Netia S.A.","status":"Operational","bands":"MVNO","notes":"MVNO on Play (P4)"},"08":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"08","operator":"E-Telko Sp. z o.o.","status":"Not operational","bands":"Unknown"},"09":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"09","brand":"Lycamobile","operator":"Lycamobile Sp. z o.o.","status":"Operational","bands":"MVNO","notes":"On Polkomtel 2G/3G network"},"10":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"10","brand":"T-Mobile","operator":"T-Mobile Polska S.A.","status":"Unknown","bands":"Unknown","notes":"former Telefony Opalenickie S.A., Sferia; CDMA 800 shut down in 2014; LTE 800 leased to Aero 2;"},"98":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"98","brand":"Play","operator":"P4 Sp. z o.o.","status":"Not operational","bands":"LTE 1800","notes":"Test network"},"11":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"11","brand":"Nordisk Polska","operator":"Nordisk Polska Sp. z o.o.","status":"Operational","bands":"CDMA2000 420"},"12":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"12","brand":"Cyfrowy Polsat","operator":"Cyfrowy Polsat S.A.","status":"Operational","bands":"MVNO","notes":"MVNO on Polkomtel"},"13":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"13","operator":"Move Telecom S.A.","status":"Unknown","bands":"Unknown","notes":"Former Sferia"},"14":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"14","brand":"Sferia","operator":"Sferia S.A.","status":"Not operational","notes":"MNC withdrawn"},"15":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"15","brand":"Aero2","operator":"Aero 2 Sp. z o.o.","status":"Operational","bands":"LTE 1800","notes":"former CenterNet S.A.; combined network with Mobyland; GSM 1800 shut down in 2010"},"16":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"16","brand":"Aero2","operator":"Aero 2 Sp. z o.o.","status":"Operational","bands":"LTE 1800","notes":"former Mobyland; combined network with CenterNet; GSM 1800 shut down in 2010"},"17":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"17","brand":"Aero2","operator":"Aero 2 Sp. z o.o.","status":"Operational","bands":"UMTS 900 / LTE 800 / TD-LTE 2600"},"18":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"18","brand":"AMD Telecom","operator":"AMD Telecom S.A.","status":"Unknown","bands":"Unknown"},"19":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"19","brand":"Teleena","operator":"Teleena Holding BV","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"20":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"20","brand":"Mobile.Net","operator":"Mobile.Net Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"21":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"21","brand":"Exteri","operator":"Exteri Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn May 2014"},"22":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"22","brand":"Arcomm","operator":"Arcomm Sp. z o.o.","status":"Unknown","bands":"Unknown"},"23":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"23","brand":"Amicomm","operator":"Amicomm Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"24":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"24","operator":"IT Partners Telco Sp. z o.o.","status":"Unknown","bands":"Unknown","notes":"former WideNet Sp. z o.o."},"25":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"25","operator":"Polskie Sieci Radiowe Sp. z o.o. Sp. k.a.","status":"Not operational","bands":"Unknown","notes":"Former Best Solutions & Technology Experience Sp. z o.o. MNC withdrawn"},"26":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"26","brand":"ATE","operator":"Advanced Technology & Experience Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"27":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"27","brand":"Intertelcom","operator":"Intertelcom Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"28":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"28","brand":"PhoneNet","operator":"PhoneNet Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"29":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"29","brand":"Interfonica","operator":"Interfonica Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"30":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"30","brand":"GrandTel","operator":"GrandTel Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn July 2016"},"31":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"31","brand":"Phone IT","operator":"Phone IT Sp. z o.o.","status":"Not operational","bands":"Unknown","notes":"MNC withdrawn"},"32":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"32","operator":"Compatel Limited","status":"Unknown","bands":"Unknown"},"33":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"33","brand":"Truphone","operator":"Truphone Poland Sp. z o.o.","status":"Operational","bands":"MVNO"},"34":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"34","brand":"NetWorkS!","operator":"T-Mobile Polska S.A.","status":"Operational","bands":"UMTS 900 / LTE 800 / LTE 1800 / LTE 2600","notes":"Shared network T-Mobile / Orange"},"35":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"35","operator":"PKP Polskie Linie Kolejowe S.A.","status":"Operational","bands":"GSM-R"},"36":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"36","brand":"Vectone Mobile","operator":"Mundio Mobile","status":"Not operational","bands":"MVNO","notes":"MNC withdrawn May 2014"},"37":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"37","operator":"NEXTGEN MOBILE LTD","status":"Unknown","bands":"Unknown"},"38":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"38","operator":"CALLFREEDOM Sp. z o.o.","status":"Unknown","bands":"Unknown"},"39":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"39","brand":"Voxbone","operator":"VOXBONE SA","status":"Operational","bands":"MVNO"},"40":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"40","operator":"Interactive Digital Media GmbH","status":"Unknown","bands":"Unknown"},"41":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"41","operator":"EZ PHONE MOBILE Sp. z o.o.","status":"Unknown","bands":"Unknown"},"42":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"42","operator":"MobiWeb Telecom Limited","status":"Unknown","bands":"Unknown"},"43":{"type":"National","countryName":"Poland","countryCode":"PL","mcc":"260","mnc":"43","operator":"Smart Idea International Sp. z o.o.","status":"Unknown","bands":"Unknown"}},"262":{"22":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"22","operator":"sipgate Wireless GmbH","status":"Unknown","bands":"MVNO"},"01":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"01","brand":"Telekom","operator":"Telekom Deutschland GmbH","status":"Operational","bands":"GSM 900 / GSM 1800/ / UMTS 2100 / LTE 800 / LTE 900 / LTE 1800 / LTE 2600","notes":"Formerly D1 - DeTeMobil, D1-Telekom, T-D1, T-Mobile"},"23":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"23","operator":"Drillisch Online AG","status":"Operational","bands":"MVNO"},"02":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"02","brand":"Vodafone","operator":"Vodafone D2 GmbH","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former D2 Mannesmann"},"03":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"03","brand":"O2","operator":"Telefónica Germany GmbH & Co. oHG","status":"Operational","bands":"GSM 900 / GSM 1800 / UMTS 2100 / LTE 800 / LTE 1800 / LTE 2600","notes":"Former E-Plus, until 2014"},"04":{"type":"National","countryName":"Germany","countryCode":"DE","mcc":"262","mnc":"04","brand":"Vodafone","operator":"Vodafone D2 GmbH","status":"R…SSH File Transfer/https://earth.google.com/earth/d/1-utcbOw4qzliHgEny3oAIPVYRTU09XHGExplore
WiGLE API
 3.1 
/swagger.json
Search, upload, and integrate statistics from WiGLE. Use API Name+Token from https://wigle.net/account

arkasha, bobzilla and uhtu - Website
Send email to arkasha, bobzilla and uhtu
Interaction with the system is governed by our EULA.
Schemes

HTTPS
Authorize
Bluetooth search and information tools

GET
​/api​/v2​/bluetooth​/detail
Get details and observation records for a single network.

GET
​/api​/v2​/bluetooth​/search
Search the WiGLE Bluetooth database.

Cell search and information tools

GET
​/api​/v2​/cell​/mccMnc
Get MCC and MNC codes for Cellular networks
GET
​/api​/v2​/cell​/search
Search the WiGLE Cell database.

Network density ageing history tools

GET
​/api​/v3​/density​/wifi
Get historical densities of WiFi networks first-seen and most-recently-seen for a geo-quad in one-year buckets.

Network observation file upload and status.

GET
​/api​/v2​/file​/kml​/{transid}
Download a KML summary of a file

GET
​/api​/v2​/file​/transactions
Get the status of files uploaded by the current user

POST
​/api​/v2​/file​/upload
Upload a file
Network search and information tools

POST
​/api​/v2​/network​/comment
Add a comment to a network

GET
​/api​/v2​/network​/detail
Get details and observation records for a single wifi or cell network

GET
​/api​/v2​/network​/geocode
Get coordinates for an address for use in searching

GET
​/api​/v2​/network​/search
Search the WiGLE Wifi database.

Statistics and information

GET
​/api​/v2​/stats​/countries
Get statistics organized by country
GET
​/api​/v2​/stats​/general
Get a named map of general upload statistics
GET
​/api​/v2​/stats​/group
Get group standings
GET
​/api​/v2​/stats​/regions
Get statistics for a specified country, organized by region, postal code, and encryption
GET
​/api​/v2​/stats​/site
Get a named map of site-level statistics
GET
​/api​/v2​/stats​/standings
Get user standings
GET
​/api​/v2​/stats​/user
Get user statistics

Stats group management

GET
​/api​/v2​/group​/admin
Get group info as a stats group administrator
GET
​/api​/v2​/group​/groupEventStats​/{groupId}
Get group member stats for a time-bounded event
GET
​/api​/v2​/group​/groupForUser​/{userName}
Get group (if present) for a user
GET
​/api​/v2​/group​/groupMembers
Get group members
User profile operations

GET
​/api​/v2​/profile​/apiToken
Get all authorization tokens for the logged-in user

GET
​/api​/v2​/profile​/user
Get the user object for the current logged-in user

v3 ALPHA

GET
​/api​/v3​/cellChannel​/{type}
Request list of channels for GSM, LTE, WCDMA, or 5G NR transmitters in specified region

GET
​/api​/v3​/detail​/bt​/{btNetworkId}
Request detail for a bluetooth network

GET
​/api​/v3​/detail​/cell​/{type}​/{operator}​/{lac}​/{cid}
Request detail for a GSM, LTE, WCDMA, or 5G NR network

GET
​/api​/v3​/detail​/cell​/CDMA​/{sid}​/{nid}​/{bsid}
Request detail for a CDMA network

GET
​/api​/v3​/detail​/wifi​/{wifiNetworkId}
Request detail for a WiFi network

Models
NetSearchResponse
WiFiNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
type	string
capabilities	[...]
userfound	boolean
device	integer($int32)
mfgrId	integer($int64)
name	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
BluetoothSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
CellSiteChannel{
channel	integer($int64)
latitude	number
longitude	number
qos	integer($int32)
}
ChannelDetailResponse{
success	boolean
resultsExceedLimit	boolean
results	[...]
resultType	string
}
MccMncRecord{
type	string
countryName	string
countryCode	string
mcc	string
mnc	string
brand	string
operator	string
status	string
bands	string
notes	string
}
CellSearchResponse{
success	boolean
totalResults	integer($int64)
first	integer($int64)
last	integer($int64)
resultCount	integer($int64)
results	[...]
searchAfter	string
Use this in future searches to get the next page of data

search_after	integer($int64)
deprecated

}
GenericNetwork{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
id	string
attributes	string
channel	integer($int32)
gentype	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
DensityAsOfDate{
date	string
firstTimeSeenDensity	integer($int64)
lastTimeSeenDensity	integer($int64)
}
DensityResponse{
histogramByCell	[...]
cells	integer($int32)
millisecondsToCalculate	integer($int64)
requestTopLat	number
requestBottomLat	number
requestLeftLon	number
requestRightLon	number
}
GeoHistogram{
topLat	number
bottomLat	number
leftLon	number
rightLon	number
densities	[...]
}
BluetoothLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
type	string
attributes	string
}
BtDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
capabilities	[...]
deviceType	integer($int32)
readOnly: true
locationClusters	[...]
}
BtLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
StreetAddress{
housenumber	string
road	string
city	string
region	string
country	string
postalcode	string
}
WiFiDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
name	string
readOnly: true
type	string
readOnly: true
comment	string
readOnly: true
bcninterval	integer($int32)
readOnly: true
freenet	string
readOnly: true
dhcp	string
readOnly: true
paynet	string
readOnly: true
encryption	string
readOnly: true
channel	integer($int32)
readOnly: true
locationClusters	[...]
}
WiFiLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
name	string
netId	string
noise	number($float)
snr	number($float)
wep	string
channel	integer($int32)
frequency	integer($int32)
encryptionValue	string
}
WiFiLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
CellDetail{
trilateratedLatitude	number
readOnly: true
trilateratedLongitude	number
readOnly: true
bestClusterWiGLEQoS	integer($int32)
readOnly: true
firstSeen	string($date-time)
readOnly: true
lastSeen	string($date-time)
readOnly: true
lastUpdate	string($date-time)
readOnly: true
streetAddress	StreetAddress{...}
networkId*	string
readOnly: true
type	string
readOnly: true
attributes	[...]
channel	integer($int32)
readOnly: true
locationClusters	[...]
xarfcn	integer($int32)
readOnly: true
}
CellLocationCluster{
centroidLatitude	number($double)
centroidLongitude	number($double)
minLastUpdate	string($date-time)
maxLastUpdate	string($date-time)
clusterSsid	string
locations	[...]
score	integer($int32)
daysObservedCount	integer($int32)
}
GenericLocation{
alt	integer($int32)
accuracy	number($float)
lastupdt	string($date-time)
latitude	number
longitude	number
month	string
ssid	string
time	string($date-time)
signal	number($float)
netId	string
genType	string
attributes	string
channel	integer($int32)
}
Group{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
authType	string
groupOwner	boolean
}
GroupMember{
groupId	string
username	string
status	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
firstTransid	string
lastTransid	string
monthCount	integer($int64)
prevMonthCount	integer($int64)
}
GroupResponse{
success	boolean
groupid	string
group	Group{...}
users	[...]
}
GroupMemberResponse{
success	boolean
users	[...]
group	Group{...}
}
GroupMemberEventStats{
userName	string
wifiDiscoveredWithLocation	integer($int64)
wifiDiscovered	integer($int64)
cellDiscoveredWithLocation	integer($int64)
cellDiscovered	integer($int64)
btDiscoveredWithLocation	integer($int64)
btDiscovered	integer($int64)
}
GroupStatsResponse{
overAllGroupStats	[...]
startDateTime	string($date-time)
endDateTime	string($date-time)
eventMemberStats	[...]
}
GeocodingResponse{
address	{...}
lat	number
lon	number
importance	number
place_id	integer($int64)
licence	string
osm_type	string
display_name	string
boundingbox	[...]
}
WiFiNetworkDetailResponse{
success	boolean
cdma	boolean
gsm	boolean
lte	boolean
nr	boolean
wcdma	boolean
wifi	boolean
addresses	[...]
results	[...]
}
WiFiNetworkWithLocation{
trilat	number
trilong	number
ssid	string
qos	integer($int32)
transid	string
firsttime	string($date-time)
lasttime	string($date-time)
lastupdt	string($date-time)
netid	string
name	string
type	string
comment	string
wep	string
bcninterval	integer($int32)
freenet	string
dhcp	string
paynet	string
userfound	boolean
channel	integer($int32)
frequency	integer($int32)
rcois	string
locationData	[...]
encryption	string
country	string
region	string
road	string
city	string
housenumber	string
postalcode	string
}
NetworkGeocodingResponse{
success	boolean
results	[...]
}
NetCommentResponse{
success	boolean
comment	string
netid	string
}
Person{
userid	string
email	string
donate	string
joindate	string($date-time)
lastlogin	string($date-time)
flags	integer($int64)
emailVerified	boolean
nextlogin	string($date-time)
session	string
admin	boolean
success	string
}
AuthToken{
authName	string
token	string
status	string
Enum:
Array [ 2 ]
type	string
Enum:
Array [ 5 ]
personId	integer($int64)
}
ResettableAuthTokenResponse{
success	boolean
result	[...]
digest	string
id	integer($int32)
}
GroupStat{
groupId	string
groupName	string
owner	string
discovered	integer($int64)
total	integer($int64)
genDisc	integer($int64)
members	integer($int64)
joined	boolean
groupOwner	boolean
}
GroupStatResponse{
success	boolean
groups	[...]
}
CountriesResponse{
success	boolean
countries	[...]
}
CountryStat{
country	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
EncryptionStat{
wep	string
count	integer($int64)
}
PostalStat{
postalCode	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
RegionResponse{
success	boolean
regions	[...]
postalCode	[...]
encryption	[...]
}
RegionStat{
region	string
wifiCount	integer($int64)
cellCount	integer($int64)
btCount	integer($int64)
}
UserStandings{
rank	integer($int64)
monthRank	integer($int64)
userName	string
discoveredWiFiGPS	integer($int64)
discoveredWiFiGPSPercent	number($float)
discoveredWiFi	integer($int64)
discoveredCellGPS	integer($int64)
discoveredCell	integer($int64)
discoveredBtGPS	integer($int64)
discoveredBt	integer($int64)
eventMonthCount	integer($int64)
eventPrevMonthCount	integer($int64)
prevRank	integer($int64)
prevMonthRank	integer($int64)
totalWiFiLocations	integer($int64)
first	string
last	string
self	boolean
}
UserStatsResponse{
success	boolean
imageBadgeUrl	string
statistics	UserStandings{...}
rank	integer($int64)
monthRank	integer($int64)
user	string
}
TransLog{
transid	string
username	string
firstTime	string($date-time)
lastupdt	string($date-time)
fileName	string
fileSize	integer($int64)
fileLines	integer($int64)
status	string
discoveredGps	integer($int64)
discovered	integer($int64)
total	integer($int64)
totalGps	integer($int64)
totalLocations	integer($int64)
percentDone	number($float)
timeParsing	integer($int64)
genDiscovered	integer($int64)
genDiscoveredGps	integer($int64)
genTotal	integer($int64)
genTotalGps	integer($int64)
genTotalLocations	integer($int64)
btDiscovered	integer($int64)
btDiscoveredGps	integer($int64)
btTotal	integer($int64)
btTotalGps	integer($int64)
btTotalLocations	integer($int64)
wwwdStatus	string
wait	integer($int64)
brand	string
model	string
osRelease	string
}
TranslogResponse{
success	boolean
results	[...]
processingQueueDepth	integer($int64)
geoQueueDepth	integer($int64)
trilaterationQueueDepth	integer($int64)
}
TransidResponse{
file	string
size	integer($int64)
transId	string
}
UploadResponse{
success	boolean
warning	string
results	UploadResultsResponse{...}
observer	string
}
UploadResultsResponse{
timeTaken	string
filesize	integer($int64)
filename	string
transids	[...]
}
ErrorMessageResponse{
success	boolean
message	string
}

The github.dev web-based editor is a lightweight editing experience that runs entirely in your browser. You can navigate files and source code repositories from GitHub, and make and commit code changes.

There are two ways to go directly to a VS Code environment in your browser and start coding:

* Press the . key on any repository or pull request.
* Swap `.com` with `.dev` in the URL. For example, this repo https://github.com/github/dev becomes http://github.dev/github/dev

Preview the gif below to get a quick demo of github.dev in action.

![github dev](https://user-images.githubusercontent.com/856858/130119109-4769f2d7-9027-4bc4-a38c-10f297499e8f.gif)

# Why?
It’s a quick way to edit and navigate code. It's especially useful if you want to edit multiple files at a time or take advantage of all the powerful code editing features of Visual Studio Code when making a quick change. For more information, see our [documentation](https://github.co/codespaces-editor-help).
