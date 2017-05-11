# App Store reviews Splunk app
The Splunk App Review app contains dashboards designed to help you analyse your apps performance. The dashboards enable you to do the following:

- Track ratings over time
- Highlight when your app reviews fall outside of the expected value
- Compare versions
- Display comments by version/rating/country/content
- Sentiment analysis of the comments

# Data format
The data should contain the following fields as illustrated by an example JSON object:
```JSON
{
  "t": "06/Apr/2017:12:11:10",
  "title": "This is a title in the original languange",
  "content": "This is the review in the orginal language! ",
  "title_en": "This is the title in English",
  "content_en": "This is the review in English",
  "id": "1234abcd5678efgh",
  "rating": 5,
  "version": "1.1.1",
  "device": "MyDevice",
  "os_version": 1.1,
  "author": "John Smith",
  "country": "GB",
  "store": "Android",
  "app_name": "MyApp"
}
```

The app expects the data to be ingested using the following Splunk conventions:
```
index=product
sourcetype=store_review
```
where the AppStore is e.g. itunes, android etc.
If you do not have this data available you may want to have a look [at our repository here](https://github.com/shazam/app-store-reviews-and-translations). This repository contains scripts for generating app review data for both iOS and Google Play store in the desired output format.
We've included some fake sample data for you to try the app with. Simply download the `SampleData.tar.gz` folder and ingest the data in the index and sourcetype given above.

# Installation
Download the splunk-app-reviews folder and copy it to ${{SPLUNK_HOME}}/etc/apps. Restart Splunk and you should be good to go!
*Note*: The app has only been tested for Splunk 6.5. Some dashboards require the sentiment analysis app which can be found [here](https://splunkbase.splunk.com/app/1179/).
The result should look something like this:
![alt text](https://raw.githubusercontent.com/shazam/app-store-reviews-and-translations/master/screenshot1.png)
![alt text](https://raw.githubusercontent.com/shazam/app-store-reviews-and-translations/master/screenshot2.png)
![alt text](https://raw.githubusercontent.com/shazam/app-store-reviews-and-translations/master/screenshot3.png)
