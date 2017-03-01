# Worldchat

A realtime chat application that displays the locations of all the chat participants on a map.

You can run your own instance of the application by first creating a Graphcool backend and then running the app locally using `npm`.


## 1. Create a Graphcool backend

```graphql
type Traveller {
  id: ID!
  createdAt: DateTime!
  updatedAt: DateTime!
  name: String!
  location: Location! @relation(name: "TravellerLocation")
  messages: [Message!]! @relation(name: "MessagesFromTraveller")
}

type Message {
  id: ID!
  createdAt: DateTime!
  updatedAt: DateTime!
  text: String!
  sentBy: Traveller!  @relation(name: "MessagesFromTraveller")
}

type Location {
  id: ID!
  createdAt: DateTime!
  updatedAt: DateTime!
  traveller: Traveller! @relation(name: "TravellerLocation")
  latitude: Float!
  longitude: Float!
}
```