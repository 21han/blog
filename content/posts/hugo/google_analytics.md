---
title: "Hugo 4 - Google Analytics Integration"
date: 2022-05-18
draft: false
weight: 103
tags: ['hugo']
TocOpen: true
ShowPostNavLinks: true
---


## How to add Google Analytics to your Hugo site?

Follow these simple steps:


### Step 1: Google Analytics Setup
1. Navigate to [Google Analytics](https://analytics.google.com/analytics/web/) and sign in your Google account (the same account as your Gmail).
2. Create an analytics **account**. You can change the **account name** anytime (I used my GitHub account name)
3. Create a **property** under your **account** by 
    1. giving your **property** a name (I used my app's name)
    2. select your industry (I selected internet industry)
    3. choose your region and time zone
    4. choose your currency
4. Create a **Data Stream** for your **Property** and fill in your website URL and provide a **Stream Name**. 
5. Use the search function to find your **Measurement ID** (in web-only properties, this is referred to as **Tracking ID** 
   in format `UA-XXXXXXX-X`), but in the newer version of Google Analytics, this is in the format `G-XXXXXXXXXX` e.g. Mine looks
   like the following. ![](https://user-images.githubusercontent.com/22876277/169631313-cc75b90c-e6c9-4054-abe9-8abfbc87f9f2.png)

### Step 2: Hugo Setup
Although differs by themes, in general. it is extremely easy to integrate your **Google Analytics** service with Hugo.

1. Check under your `themes` folder if path `<theme-name>/layouts/partials/head.html` (or `<theme-name>/layouts/partials/head.htmls`) exists.
    - If it does, check if inside that `.html` file it contains the following code chunk 
        ```
        {{- template "_internal/google_analytics.html" . }}
        ```
    - If it doesn't, create the following file under your root directory `layouts/partials/head.html`, and copy below
    code over
        ```
        <head>
            {{ template "_internal/google_analytics.html" . }}
            {{ template "_internal/google_analytics_async.html" . }}
        </head>
        ```

2. If we pass both checks, simply add **googleAnalytics** field and value to your **config.yml** file.
    ```
    buildFuture: false
    buildExpired: false
    enableEmoji: true
    
    googleAnalytics: G-xxxxxxxxx  # add your Measurement ID / Tracking ID here 
    minify:
        disableXML: true
    
    languages:
        en:
            languageName: "English"
    ```

### Step 3: Verification and Test

How can we verify if the above setup was successful or not? 

1. Navigate to the **Realtime** report in the **Reports** tab.  
2. Navigate to your site (local server is fine), and click on several posts of yours.
3. Wait for a minute or so and check if the **Users in Last 30 Minutes** changed from value 0 to 1. For my case, it took
   about 10 seconds to reflect the change.
   ![](https://user-images.githubusercontent.com/22876277/169633046-e1374f55-2e3a-4e48-8b20-00cdc5dd2fa0.png)
4. Once you have verified that everything works locally, you should feel confident to deploy the code to production.