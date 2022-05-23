# fan_certification_firebase
firebase functions and hosting for fan_certification

## 0. testing on local by running emulator
[Document](https://firebase.google.com/docs/functions/local-emulator)

## 1-1. functions
- addHeart
    - input: platform(*String*, default value: "0"), account(*String*, ChannelID for YouTube)
    - function: increases the like by 1 when 5 minutes or more pass from the 'recent' using the 'recent' inside the 'celeb', or outputs an error to try again after a while

- manageFollow
    - input: platform(*String*, default value: "0"), account(*String*, ChannelID for YouTube), method(*String*, "add", "update" or "delete"), title(*String?*, channel name), profileURL(*String?*, thumbnail url)
    - function: 
        - add
            adds celebrities to 'celeb' in my account. length of 'celeb' cannot be more than three and values of 'celeb' cannot be duplicated.

        - update
            updates title and url of celeb. Currently, there are Title and url for each celeb, but it will be integrated into one later. See to-do list.

        - delete (doesn't need title and url)
            deletes celebrities in 'celeb' in user's account and decrease related celeb's follow and likes

    **To-do list**
    [ ] **(important)** In the case of title and url, it is not saved for each celebrity in each account, but it is saved in a celebrity on "YouTube" or "Instagram" collection to eliminate duplication.

- initUser
    - input: None
    - function: sets default values such as "celeb: []" if user is not in "Users" collection

- deleteAccount
    - input: None
    - function: deletes user's account in the "Users" collection and initializes all user have followed and clicked likes

## 1-2. output structure of functions
- case success
    - {status: 200, message: "success"}
- case error
    - {status: 400, message: "{message of error}"}

## 2. hosting (Getting ready...)