---
layout: page_v2
title: Global Targeting Parameters - iOS
description: Prebid Mobile API global targeting parameters for iOS
top_nav_section: prebid-mobile
nav_section: prebid-mobile
sidebarType: 2
---

# Global Targeting Parameters
{:.no_toc}

Prebid Mobile supports the following global targeting parameters. These targeting parameters are set only once and apply to all Prebid Mobile ad units. They do not change for a given user session.

* TOC
{:toc}

## Global User Targeting

### Gender

```
public var gender:Gender 
```

gender is an enum with the following values: 

```

public enum Gender: String { 
    case unknown
    case male
    case female
}
```

You can retrieve and set the gender for targeting:

```
let gender = Targeting.shared.gender 

//do something with gender
```

```
Targeting.shared.gender = .unknown;
```

### Year of Birth

```
public var yearofbirth:Int? 
```

You can retrieve and set the year of birth for targeting:

```
if let yob = Targeting.shared.yearofbirth { 
    //do something with yob
};

guard let yob = Targeting.shared.yearofbirth else { 
    print("There was an error retrieving year of birth)
    return 
}

//do something with yob
```

```
Targeting.shared.yearofbirth = 1990;
```

### User Keywords

User keywords are a list of keywords, intrests or intent as defined by user.keywords in OpenRTB 2.5. Any keywords passed in the UserKeywords object may be passsed to DSPs.

#### Add User Keyword

```
func addUserKeyword(_ newElement: String)
```

#### Add User Keywords

```
func addUserKeywords(_ newElements: Set<String>)
```

#### Remove User Keywords

```
func removeUserKeyword(_ element: String)
```

#### Clear User Keywords

```
func clearUserKeywords()
```

Examples:

```swift
Targeting.shared.addUserKeyword("globalUserKeywordValue1")
Targeting.shared.addUserKeyword("globalUserKeywordValue2")
Targeting.shared.addUserKeyword("globalUserKeywordValue3")
```

```objective_c
[Targeting.shared addUserKeyword:@"globalUserKeywordValue1"];
[Targeting.shared addUserKeyword:@"globalUserKeywordValue2"];
[Targeting.shared addUserKeyword:@"globalUserKeywordValue3"];
```

## Global Application Targeting


### Domain 

Retrieve and set the domain of your app with the following commands:

```
Targeting.shared.domain
```
```
Targeting.shared.domain = domain
```
### Store URL

Retrieve and set the domain of your store URL with the following commands: 

```
Targeting.shared.storeURL
```

```
Targeting.shared.storeURL = "itunes store URL string"
```

### iTunesID

Retrieve and set the domain of your store URL with the following commands: 

```
Targeting.shared.itunesID
```

```
Targeting.shared.itunesID = itunesID
```

## Inventory (Context) Keywords

Context Keywords are a list of keywords about the app as referenced in OpenRTB 2.5 as app.keywords. Any keyword passed in the context keyword field may be passed to the buyer for targeting.

### Add Context Keyword

```
func addContextKeyword(_ newElement: String)
```

### Add Context Keywords

```
func addContextKeywords(_ newElements: Set<String>)
```

### Remove Context Keywords

```
func removeContextKeyword(_ element: String)
```

### Clear Context Keywords

```
func clearContextKeywords()
```

Examples:

Swift
```swift
Targeting.shared.addContextKeyword("globalContextKeywordValue1")
Targeting.shared.addContextKeyword("globalContextKeywordValue2")
Targeting.shared.addContextKeyword("globalContextKeywordValue3")
```

Objective C
```objective_c
[Targeting.shared addContextKeyword:@"globalContextKeywordValue1"];
[Targeting.shared addContextKeyword:@"globalContextKeywordValue2"];
[Targeting.shared addContextKeyword:@"globalContextKeywordValue3"];
```

## First Party Data

First Party Data (FPD) is free form data supplied by the publisher to provide additional targeting of the user or inventory context, used primarily for striking PMP (Private MarketPlace) deals with Advertisers. Data supplied in the data parameters are typically not sent to DSPs whereas information sent in non-data objects (i.e. setYearOfBirth, setGender, etc.) will be. Access to FPD can be limited to a supplied set of Prebid bidders via an access control list.

Data is broken up into two different data types:

* User
    * Global in scope only
* Inventory (context)
    * Global scope
    * Ad Unit grain

 The below first party user and inventory context will apply to all ad units. For ad unit level first party data, refer to [First Partay Data section in the Ad Unit](pbm-adunit-ios#first-party-data) page.

### First Party User Data

#### Add User Data

```
func addUserData(key: String, value: String)
```

#### Update User Data

```
func updateUserData(key: String, value: Set<String>) 
```

#### Remove User Data

```
func removeUserData(forKey: String)
```

#### Clear User Data

```
func clearUserData()
```

Examples:

Swift
```swift
Targeting.shared.addUserData(key: "globalUserDataKey1", value: "globalUserDataValue1")
```

Object C
```objective_c
[Targeting.shared addUserDataWithKey:@"globalUserDataKey1" value:@"globalUserDataValue1"];
```

### First Party Inventory (Context) Data

#### Add Context Data

```
func addContextData(key: String, value: String)
```

#### Update Context Data

```
func updateContextData(key: String, value: Set<String>)
```

#### Remove Context Data

```
func removeContextData(forKey: String)
```

#### Clear Context Data

```
func clearContextData()
```

Examples:

Swift
```swift
Targeting.shared.addContextData(key: "globalContextDataKey1", value: "globalContextDataValue1")
```

Objective C
```objective_c
[Targeting.shared addContextDataWithKey:@"globalContextDataKey1" value:@"globalContextDataValue1"];
```

#### Ad Unit Context Data
For ad unit context data, please refer to the [ad unit](pbm-adunit-ios.html) section.

### Access Control
The First Party Data Access Control List provides a method to restrict access to first party data to a supplied list of bidders.

#### addBidderToAccessControlList

```
func addBidderToAccessControlList(_ bidderName: String)
```

#### removeBidderFromAccessControlList

```
func removeBidderFromAccessControlList(_ bidderName: String)
```

#### clearAccessControlList

```
func clearAccessControlList()
```

Examples:

Swift
```swift
Targeting.shared.addBidderToAccessControlList(Prebid.bidderNameRubiconProject)
```

Objective C
```objective_c
[Targeting.shared addBidderToAccessControlList: Prebid.bidderNameRubiconProject];
```



## GPDR

Prebid Mobile supports the [IAB GDPR recommendations](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/Mobile%20In-App%20Consent%20APIs%20v1.0%20Draft%20for%20Public%20Comment.md). For a general overview of Prebid Mobile support for GDPR, see [Prebid Mobile Guide to European Ad Inventory and Providing Notice, Transparency and Choice]({{site.github.url}}/prebid-mobile/gdpr.html)

### Subject To GPDR

```
public var subjectToGDPR:Bool?
```

You can retrieve and set the subjectToGDPR for targeting:

```
if let subjectToGDPR = Targeting.shared.subjectToGDPR { 
    //do something with subjectToGDPR
};

guard let subjectToGDPR = Targeting.shared.subjectToGDPR else { 
    print("There was an error retrieving subjectToGDPR)
    return 
}

//do something with subjectToGDPR

```

```
Targeting.shared.subjectToGDPR = false
```

### GDPR Consent String

```
public var gdprConsentString?
```

You can retrieve and set the subjectToGDPR for targeting:

```
if let gdprConsentString = Targeting.shared.gdprConsentString { 
    //do something with gdprConsentString
};

guard let gdprConsentString = Targeting.shared.gdprConsentString else { 
    print("There was an error retrieving gdprConsentString)
    return 
}

//do something with gdprConsentString

```

```
Targeting.shared.gdprConsentString = "A String"
```

### Subject to COPPA

Prebid supports passing of the Child Online Privacy Prection (COPPA) signal to Prebid Server (PBS) for all COPPA traffic. When PBS receives the COPPA flag we strip out all personal data from the requeset. For a general overview of COPPA, see the [FTC's guidlines](https://www.ftc.gov/enforcement/rules/rulemaking-regulatory-reform-proceedings/childrens-online-privacy-protection-rule).

```swift
var subjectToCOPPA: Bool
```

Example:

SWIFT
```
Targeting.shared.subjectToCOPPA = true
```

Objective C
```
Targeting.shared.subjectToCOPPA = true;
```

## Further Reading

- [Prebid Mobile API - iOS]({{site.baseurl}}/prebid-mobile/pbm-api/ios/pbm-api-ios.html)
- [Prebid Mobile API - Android]({{site.baseurl}}/prebid-mobile/pbm-api/android/pbm-api-android.html)




