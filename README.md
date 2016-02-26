# Storefront Assistant

This is a simple class to assist in the conversion of a Storefront Identifier (from SKCloudServiceController) into a standard ISO country code for use with the iTunes Search API.

## Installation

Just include the `StorefrontAssistant.swift` and `StorefrontCountries.plist` in your iOS 9.3 compatible project.

## Example Usage

	StorefrontAssistant.countryCode { (countryCode, error) in
	    if let error = error {
	        NSLog("Error: \(error)")
	    }
	    if let countryCode = countryCode {
	        NSLog("Country code: \(countryCode)")
	    }
	}

Storefront Assistant will automatically request permissions to access the Media Library and then fetch the current storefront identifier for the logged in user. If there are any issues (i.e. permissions denied, no connectivity, country code can't be found) then an `NSError` will be returned.

## Use case

If you want to either play Apple Music or save an Apple Music track to the user's media library, you will need to know which country they are in so you can find the relevant track identifier via the [iTunes Search API](https://affiliate.itunes.apple.com/resources/documentation/itunes-store-web-service-search-api/). The only way to know which country the logged in user's Apple Music account is with is to use the `SKCloudServiceController` method `requestStorefrontIdentifierWithCompletionHandler:` which will give you an identifier to match up to the store. Using this class, you can do a simple compare against the list which was parsed from [Apple's iTunes Affliate Links website](https://affiliate.itunes.apple.com/resources/documentation/linking-to-the-itunes-music-store/).

## Learn more

- [iOS 9.3 Music Library Additions](https://bendodson.com/weblog/2016/02/23/details-on-ios-9-3-media-library-additions/)
- [Introducing Storefront Assistant](https://bendodson.com/weblog/2016/02/26/storefront-additions-skcloudservicecontroller-to-country-code/)
- [Your iOS Music Library is a security and privacy risk](https://bendodson.com/weblog/2016/01/13/your-music-library-is-a-security-and-privacy-risk-on-ios/)