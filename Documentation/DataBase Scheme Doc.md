# Database Schema for EO-Backend
The following database schema describes how the platform allows users to create profiles, showcase their work, create and publish articles, and monetize their content by offering exclusive access and perks to their supporters.

## Users Collection
The Users collection stores the basic information about each user, including their first name, last name, age, sex, address, bio, and login credentials.

Users Collection:

    _id: unique identifier for each user
    
    firstname: string representing user's first name
    
    lastname: string representing user's last name
    
    age: integer representing user's age
    
    sex: string representing user's gender
    
    address: string representing user's address
    
    bio: string representing user's biography

Code Example:
```js 
{
  _id: ObjectId,              // unique identifier for the user
  firstName: String,          // user's first name
  lastName: String,           // user's last name
  age: Number,                // user's age
  sex: String,                // user's sex
  address: String,            // user's address
  bio: String,                // user's bio
  email: String,              // user's email address
  password: String,           // user's password
  createdAt: Date,            // timestamp of user's account creation
  updatedAt: Date             // timestamp of user's last account update
}
 ``` 


 ## Realizations Collection
The Realizations collection stores the realizations created by each user, including their link, description, and picture.

Realizations Collection:

    _id: unique identifier for each realization
    
    userId: reference to the user who created the realization
    
    link: string representing link to the realization
    
    description: string representing the description of the realization
    
    picture: string representing the URL of the picture associated with the realization

Code Example:

```js
{
  _id: ObjectId,              // unique identifier for the realization
  userId: ObjectId,           // reference to the user who created the realization
  link: String,               // link to the realization (e.g., portfolio website, YouTube video, etc.)
  description: String,        // description of the realization
  picture: String,            // URL of the picture representing the realization
  createdAt: Date,            // timestamp of realization's creation
  updatedAt: Date             // timestamp of realization's last update
}

```

## Articles & Comments Collection
The Articles collection stores the articles created by each user, including their text, pictures, video links, and comments.

Articles Collection:

    _id: unique identifier for each article
    userId: reference to the user who created the article
    title: string representing the title of the article
    text: string representing the main text of the article
    picture: string representing the URL of the picture associated with the article
    videoLink: string representing the URL of the video associated with the article (if any)

Comments Collection:

    _id: unique identifier for each comment
    articleId: reference to the article the comment is associated with
    userId: reference to the user who created the comment
    text: string representing the text of the comment

Code Example:
```js
{
  _id: ObjectId,              // unique identifier for the article
  userId: ObjectId,           // reference to the user who created the article
  title: String,              // title of the article
  text: String,               // text content of the article
  pictures: [String],         // array of URLs of pictures included in the article
  videoLinks: [String],       // array of URLs of videos included in the article
  comments: [{
    userId: ObjectId,         // reference to the user who posted the comment
    text: String,             // text content of the comment
    createdAt: Date,          // timestamp of the comment's creation
    updatedAt: Date           // timestamp of the comment's last update
  }],
  createdAt: Date,            // timestamp of article's creation
  updatedAt: Date             // timestamp of article's last update
}

```

## User Followers Collection
The User Followers collection stores the followers of each user. Each follower document contains the reference to the user who is following, the reference to the user who is being followed, and a timestamp of when the follower relationship was created.

Code Example:
```js
{
  _id: ObjectId,              // unique identifier for the follower relationship
  followerUserId: ObjectId,   // reference to the user who is following
  followedUserId: ObjectId,   // reference to the user who is being followed
  createdAt: Date             // timestamp of follower relationship's creation
}

```

## User Donations Collection
The User Donations collection stores the donations made by each user to other users. Each donation document contains the reference to the user who made the donation, the reference to the user who received the donation, the amount of the donation, and a timestamp of when the donation was made.

Code Example:
```js
{
  _id: ObjectId,              // unique identifier for the donation
  fromUserId: ObjectId,       // reference to the user who made the donation
  toUserId: ObjectId,         // reference to the user who received the donation
  amount: Number,             // amount of the donation
  createdAt: Date             // timestamp of donation's creation
}

```
