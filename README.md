hackathon.json Specification
----------------------------

A standard data format for publishing evidence of public participation in technical events.

# Overview

Our goals are to have a shared and linked metadata and data model for opening data from and about hackathons. Here we describe how this may be published in the [JSON serialization for Linked Data](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://json-ld.org/&ved=2ahUKEwifyq272qGJAxV48LsIHe-qFuMQFnoECAgQAQ&usg=AOvVaw0KYV5lDp9ZQ0M18tp93C6E) (JSON-LD, or just `json`) format. 

# Basic type

The data model for `hackathon.json` is based on the [Hackathon type](https://schema.org/Hackathon) at Schema.org, which defines the properties and sub-entities involved in describing an event of this type. 

The essentials of this is a header that includes a `@context` and `@type` reference, along with top-level properties such as `name` and `startDate`, as follows:

```
{
  "@context": "http://schema.org",
  "@type": "Hackathon",
  "name": "GLAMhack 2024",
  "startDate": "2024-09-06T09:00",
  "endDate": "2024-09-07T16:00",
  ...
}
```

# Location

The geographic location of the event, if it has a physical address or geocoordinates, can be documented with the [Location](https://schema.org/location) property, which may be formatted as a `Place`, `PostalAddress`, `VirtualLocation`, or just be a plain `Text` description.

# Offers

Using the [offers](https://schema.org/offers) property, we can describe requirements of joining the hackathon, just as the obligation to buy a ticket or join a waiting list.

# CreativeWork

The Schema.org type proposes the use of [CreativeWork](https://schema.org/CreativeWork) sub-entities to document the results of an event. This would include a `@context`, as well as `name`, `dateCreated` and so on. You can see this in the example below.

# Full example

Retrieved from https://hack.glam.opendata.ch/hackathon.json on 2024-10-22:

```
{
  "@context": "http://schema.org",
  "@type": "Hackathon",
  "name": "GLAMhack 2024",
  "startDate": "2024-09-06T09:00",
  "endDate": "2024-09-07T16:00",
  "description": "10th Swiss Open Cultural Data Hackathon in Luzern",
  "mainEntityOfPage": "https://opendata.ch/de/events/glamhack24/",
  "url": "https://hack.glam.opendata.ch/event/12",
  "image": "https://s3.dribdat.cc/odch/a/1771/IBXKQB3UD3XW2PFOVONZNBX8/OpenGLAM_CH_Logo.svg.png",
  "location": {
    "@type": "Place",
    "address": "Lucerne",
    "name": "OpenGLAM CH"
  },
  "offers": {
    "@type": "Offer",
    "url": "https://opendata.ch/de/events/glamhack24/"
  },
  "workPerformed": [
    {
      "@type": "CreativeWork",
      "name": "DeepGLAM",
      "dateCreated": "2024-09-02T06:28",
      "dateModified": "2024-09-15T16:13",
      "description": "A \"meta\" challenge, in the form of a visualization that encourages participants to share some feedback/thoughts about this platform",
      "discussionUrl": "https://github.com/we-art-o-nauts/DeepGLAM/issues",
      "image": "https://s3.dribdat.cc/glam/c/1/JWWCD87JGB82LF0358POUQX8/Screenshot_from_20240906_220057.jpg",
      "license": "https://creativecommons.org/licenses/by/4.0/",
      "url": "https://hack.glam.opendata.ch/project/300"
    },
    ...
  ]
}
```

# Related standards

- [Frictionless Data](https://frictionlessdata.io) 
- [Open Event Data](https://www.openeventdata.ch)
- [Dublin Core™](https://www.dublincore.org/specifications/dublin-core/)
- [Dribdat API](https://dribdat.cc/contribute.html#api-guide) (see [issue #112](https://github.com/dribdat/dribdat/issues/112))

# Tools

The following applications can generate a `hackathon.json`, visualize the format, or validate your schema:

- [Schema Validator](https://validator.schema.org/) (Validator at Schema.org)
- [Schemantra](https://www.schemantra.com/schema_list/Hackathon) (Generator: fill out a form)
- [Dribdat](https://codeberg.org/dribdat/dribdat) (Generator: a Python tool for hackathons)
- [Backboard](https://codeberg.org/dribdat/backboard) (Viewer: a JavaScript renderer, part of Dribdat)

# License

[CC0 1.0 Universal](LICENSE)