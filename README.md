# Game Review Feed JSON Specification

## Table of index

## Goal

The goal of this specification is to create a simple but universal structure on how to expose game reviews by a reviewer
so that any it can be programmatically crawled, aggregated and exposed on other web services.

This goal shares the similar goal RSS/Atom has regarding exposing published content, but is specifically aimed for game reviews.

By creating a standard, it would help;

- Review publishers, as it makes it easier to expose their review content to a larger audience, hence draw in traffic to their site.

- Content aggregators, as feed aggregator services will be able to programmatically fetch reviews from different sources for a certain
game, giving the reader a broader selecting of different game opinions and game reviews.



# Feed example

https://www.reviewpublisher.com/reviews.json

```json
{
  "version": 1,
  "reviews": [
    {
      "gameName": "Diablo 3",
      "gamePlatform": "PC",
      "gameReleaseYear": 2012,
      "link": "https://www.reviewpublisher.com/review/diablo-3-latest-smashhit-from-blizzard",
      "score": 78,
      "maxScore": 100,
      "published": "2018-10-22T10:45:43+00:00"
    },
    {
      "gameName": "Doom",
      "gamePlatform": "PC",
      "gameReleaseYear": 1993,
      "link": "http://oldreviews.reviewpublisher.com/doom.html?utm_source=reviewfeed&utm_medium=reviewlink",
      "score": 4,
      "maxScore": 10,
      "published": "1994-02-12"
    }
  ]
}
```



## Specifications

### Feed structure

#### Top level

Specification of the top level JSON object and its properties:

- `version` (required) (number) - Should be the current specification version the feed is using, currently version `1`
- `reviews` (required) (array of objects) - An array of review items.

#### Review item

Specification of each review item object and its properties:

- `gameLabel` (required) (string) - The canonical name of the game, according to it's publisher and or developer.
- `gamePlatform` (required) (string) - The English name of the gaming platform where the game was released on, such as `PC`, `Nintendo Switch`, `Playstation 4`, `NES`, `XBOX 360`, `iOS`, etc. In order to keep the standard future proof, we only ask the review publishers to be clear and non-ambigious with what platform they mean, as it will help feed readers organize the reviews.
-  `gameReleaseYear` (required) (number) - The year the game was released. This will help feed readers differentiate between  games that share the same name and platform (such as 1993's and 2016's `Doom` which was both released on same platforms as well). 
- `link` (required) (string) - The web URI (`https://` or `https://`) to where the review is published, and which the content readers should be directed to.
- `score` and `maxScore` (optional) (number) - If the review publisher has given any numeric review score and what the max score is to give.

- `published` (required) (string) - An [ISO-8601 date](https://en.wikipedia.org/wiki/ISO_8601) when the review was published.

### Character encoding

The feed should be encoded in [UTF-8](https://en.wikipedia.org/wiki/UTF-8).

### MIME

The feed should be served using the MIME type `application/json`, the same content type as any other JSON data 


## Suggestions for review publishers

### Publishing, access and update frequency of the feed

There are no requirements regarding how the feed is published. For example `reviewpublisher.com/reviews.json`, `reviewpublisher.com/reviews` and `reviews.reviewpublisher.com` would be perfectly legal URIs to access the feed.

Access constraints may be applied on the feed by the reviewer, however one could argue that it would be in the 
reviewer's best interest to expose the feed publically in order to maximize their review content.

There are neither any requirements regarding update frequencies.

### Faulty data

It would be in the reviewer publisher's best interest to keep the feed free from JSON errors, clean and of high quality content, with working outbounding links, as it is up to any feed readers to judge if its worth reading the feed.


# Reviewers

The authors thank the following people for their extensive contributions and review, in alphabetical order: 
