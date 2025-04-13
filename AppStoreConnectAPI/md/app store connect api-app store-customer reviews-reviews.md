

- App Store Connect API
- App Store
-  Customer Reviews 

API Collection

# Customer Reviews

Get the customer reviews for your app.

## Overview

The `customerReviews` resource represents the ratings and reviews that customers write for your app that the App Store displays. Customers can provide reviews for your app in the App Store, or when your app requests a review. For more information about reviews, see Ratings, Reviews, and Responses.

Use this API to read the customer reviews for your app as follows:

- Call the List All Customer Reviews for an App endpoint to get all customer reviews for your app. Filter the reviews by territory and rating, and sort them by date or rating. You can also get a list of the reviews with or without published responses.

- Call the List All Customer Reviews for an App Store Version endpoint to get the customer reviews for a specific app version.

- Call the Read Customer Review Information endpoint using the resource ID of the review to read the details of a specific review.

To manage your responses to the customers reviews, use the endpoints in Customer Review Responses. For example, call Get a Customer Review Response using the resource ID of the customer review to read your response to that review.

## Topics

### Getting Customer Reviews for an App or App Version

List All Customer Reviews for an App

Get a list of customer reviews for a specific app.

List All Customer Reviews for an App Store Version

Get a list of customer reviews for a specific version of your app.

### Reading Customer Reviews

Read Customer Review Information

Get information about a specific customer review, including the review content.

### Objects

object CustomerReviewsResponse

A response that contains a list of Customer Reviews resources.

object CustomerReviewResponse

A response that contains a single Customer Review resource.

object CustomerReview

The data structure that represents a Customer Reviews resource.

## See Also

### Customer Reviews and Responses

Customer Review Responses

Get, create, update, and delete your responses to customer reviews.

