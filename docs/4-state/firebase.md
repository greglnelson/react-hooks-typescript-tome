---
layout: default
title: Firebase
nav_order: 4.3
parent: Using State
---

# Firebase Setup

[&laquo; Return to State](index.md)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Firebase and Firestore

Firebase is a google combination service that has various tools. In this sub-chapter we'll be talking about the `Firestore`, a `nosql` databse.
`Nosql` databases are a way to store information in an organized way, but as its namesake does not follow many of the SQL mechanics such as field relations or restrictions.
Everything is controlled by the programmer from the data format to how those pieces of data relate to each other. This leaves some more opportunity for the final result
to have problems since all the gaurdrails are off. But it's also extremely easy to add or retrieve information from such databases.

## Getting set up

Before working with Firebase you'll need to not only get a Firebase webapp going but also to install the emulator.

Here is a walk-through video (an updated version) that goes through these steps from the perspective of starting with a fresh react project.

![Firebase setup Video](https://video.maine.edu/media/Setting%20Up%20Firebase/1_0kgpvmqm)

It goes over:
* Getting a Firebase Project started
* Installing Firebase Emulators
* Installing the modules needed for Testing
* Creating a Button that adds to the database
* Creating a test that confirms the Button sends info to the database.

## Additional Firebase Example

![Getting-started-with-Firebase repository](https://github.com/TSchotter/Getting-started-with-Firebase)

The getting-started-with-firebase repository has a more complex example containing:
* Adding to the database
* Reading from the database dynamically (it will update as soon as there is new info)
* Updating values in the database
* Tests for all of the above

# Firebase Exercise

Now it's time to try it out for yourself with some goals.

First you're going to be starting from a fresh repository clone, so make sure you're in a directory where you want this new repository to be.

```sh
$> git clone https://github.com/COS420-Fall24/cos420-broken-firebase.git
$> cd cos420-broken-firebase
$> git checkout -b solved-firebase
$> npm i
```

If you look at the file structure, most of the setup files have been made for you except the config file will look like this:

```typescript
const firebaseConfig = {
  apiKey: "x",
  authDomain: "x",
  projectId: "x",
  storageBucket: "x",
  messagingSenderId: "x",
  appId: "x"
};
```

Make sure you replace that with your own webapp info.

You will also need to initialize Firebase in this directory, including the emulators.

## Goals

### Add info to the database

There are four components in the `components` directory. The one in control of adding information to the database is the `AddPerson` component.

There are two parts to add information to:

```typescript
async function createPerson(person: person){
    // Add the person document to the "people" collection
}
```

```typescript
<button onClick={()=>{
    //Gather the infomation from the other input fields and send them to the createPerson function, as a person
}}>Add Person</button>
```

Both of these parts will be making use of the `person` interface that's stored in the `models` directory.

```typescript
export type roleType = "Instructor" | "Student" | "TA";
export interface person {
    fname: string;
    lname: string;
    role: roleType;
}
```

The goal is to make it so that the button, when clicked, will pull information from the input fields (and select field), and send it to the db to be added.

Make sure you have your emulator running.

### Gather info from the database

The last three components are designed to show the values of each of their respective roles.

```typescript
function InstructorList() {
    return (
        <div>
            <h2>Instructor:</h2>
            {/* 
            Query for all persons with a role of "Instructor" here.
            Map out the results into their own tags
            */}

        </div>
    )
}
```

The data that they are expecting from that database is based on `person.tsx` in the `models` directory:

Fix each of these components so that they show a full list of persons in each category.

### Create Tests for each of the components

For each of the four components, write tests that confirms that they are either displaying expected information or are adding expected information to the database.

Before ever interacting with the database during your tests, make sure you delete everything inside of it. Don't do this manually, make this part of your tests.

Continue practicing good github habits with `git add`/`git commit` or the Visual Studio Code interface to make small regular commits.