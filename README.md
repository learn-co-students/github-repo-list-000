---
tags: networking, apis
language: objc
---

# Github Repo List

In this lab your goal is to write a github repository browser. To do this we are going to need to talk to the github repo API, parse the results and then display them in a `UITableView`.

## The API

The API is actually pretty simple. First you need to get a client_id and client_secret, but you can probably use mine and it'll be fine. To get a list of all repositories just do the following request:

```
GET https://api.github.com/repositories?client_id=f523187ecd099eecc17d&client_secret=784bc46e9c6d412b31d6dfab7d798d1078472603
```

and you'll get a response like this

```
[
  {
    "id": 1,
    "name": "grit",
    "full_name": "mojombo/grit",
    "owner": {
      "login": "mojombo",
      "id": 1,
      "avatar_url": "https://avatars.githubusercontent.com/u/1?",
      "gravatar_id": "25c7c18223fb42a4c6ae1c8db6f50f9b",
      "url": "https://api.github.com/users/mojombo",
      "html_url": "https://github.com/mojombo",
      "followers_url": "https://api.github.com/users/mojombo/followers",
      "following_url": "https://api.github.com/users/mojombo/following{/other_user}",
      "gists_url": "https://api.github.com/users/mojombo/gists{/gist_id}",
      "starred_url": "https://api.github.com/users/mojombo/starred{/owner}{/repo}",
      "subscriptions_url": "https://api.github.com/users/mojombo/subscriptions",
      "organizations_url": "https://api.github.com/users/mojombo/orgs",
      "repos_url": "https://api.github.com/users/mojombo/repos",
      "events_url": "https://api.github.com/users/mojombo/events{/privacy}",
      "received_events_url": "https://api.github.com/users/mojombo/received_events",
      "type": "User",
      "site_admin": false
    },
    "private": false,
    "html_url": "https://github.com/mojombo/grit",
    "description": "**Grit is no longer maintained. Check out libgit2/rugged.** Grit gives you object oriented read/write access to Git repositories via Ruby.",
    "fork": false,
    "url": "https://api.github.com/repos/mojombo/grit",
    "forks_url": "https://api.github.com/repos/mojombo/grit/forks",
    "keys_url": "https://api.github.com/repos/mojombo/grit/keys{/key_id}",
    "collaborators_url": "https://api.github.com/repos/mojombo/grit/collaborators{/collaborator}",
    "teams_url": "https://api.github.com/repos/mojombo/grit/teams",
    "hooks_url": "https://api.github.com/repos/mojombo/grit/hooks",
    "issue_events_url": "https://api.github.com/repos/mojombo/grit/issues/events{/number}",
    "events_url": "https://api.github.com/repos/mojombo/grit/events",
    "assignees_url": "https://api.github.com/repos/mojombo/grit/assignees{/user}",
    "branches_url": "https://api.github.com/repos/mojombo/grit/branches{/branch}",
    "tags_url": "https://api.github.com/repos/mojombo/grit/tags",
    "blobs_url": "https://api.github.com/repos/mojombo/grit/git/blobs{/sha}",
    "git_tags_url": "https://api.github.com/repos/mojombo/grit/git/tags{/sha}",
    "git_refs_url": "https://api.github.com/repos/mojombo/grit/git/refs{/sha}",
    "trees_url": "https://api.github.com/repos/mojombo/grit/git/trees{/sha}",
    "statuses_url": "https://api.github.com/repos/mojombo/grit/statuses/{sha}",
    "languages_url": "https://api.github.com/repos/mojombo/grit/languages",
    "stargazers_url": "https://api.github.com/repos/mojombo/grit/stargazers",
    "contributors_url": "https://api.github.com/repos/mojombo/grit/contributors",
    "subscribers_url": "https://api.github.com/repos/mojombo/grit/subscribers",
    "subscription_url": "https://api.github.com/repos/mojombo/grit/subscription",
    "commits_url": "https://api.github.com/repos/mojombo/grit/commits{/sha}",
    "git_commits_url": "https://api.github.com/repos/mojombo/grit/git/commits{/sha}",
    "comments_url": "https://api.github.com/repos/mojombo/grit/comments{/number}",
    "issue_comment_url": "https://api.github.com/repos/mojombo/grit/issues/comments/{number}",
    "contents_url": "https://api.github.com/repos/mojombo/grit/contents/{+path}",
    "compare_url": "https://api.github.com/repos/mojombo/grit/compare/{base}...{head}",
    "merges_url": "https://api.github.com/repos/mojombo/grit/merges",
    "archive_url": "https://api.github.com/repos/mojombo/grit/{archive_format}{/ref}",
    "downloads_url": "https://api.github.com/repos/mojombo/grit/downloads",
    "issues_url": "https://api.github.com/repos/mojombo/grit/issues{/number}",
    "pulls_url": "https://api.github.com/repos/mojombo/grit/pulls{/number}",
    "milestones_url": "https://api.github.com/repos/mojombo/grit/milestones{/number}",
    "notifications_url": "https://api.github.com/repos/mojombo/grit/notifications{?since,all,participating}",
    "labels_url": "https://api.github.com/repos/mojombo/grit/labels{/name}",
    "releases_url": "https://api.github.com/repos/mojombo/grit/releases{/id}"
  },
  {
    "id": 26,
    "name": "merb-core",
    "full_name": "wycats/merb-core",
    "owner": {
      "login": "wycats",
      "id": 4,
      "avatar_url": "https://avatars.githubusercontent.com/u/4?",
      "gravatar_id": "428167a3ec72235ba971162924492609",
      "url": "https://api.github.com/users/wycats",
      "html_url": "https://github.com/wycats",
      "followers_url": "https://api.github.com/users/wycats/followers",
      "following_url": "https://api.github.com/users/wycats/following{/other_user}",
      "gists_url": "https://api.github.com/users/wycats/gists{/gist_id}",
      "starred_url": "https://api.github.com/users/wycats/starred{/owner}{/repo}",
      "subscriptions_url": "https://api.github.com/users/wycats/subscriptions",
      "organizations_url": "https://api.github.com/users/wycats/orgs",
      "repos_url": "https://api.github.com/users/wycats/repos",
      "events_url": "https://api.github.com/users/wycats/events{/privacy}",
      "received_events_url": "https://api.github.com/users/wycats/received_events",
      "type": "User",
      "site_admin": false
    },
    "private": false,
    "html_url": "https://github.com/wycats/merb-core",
    "description": "Merb Core: All you need. None you don't.",
    "fork": false,
    "url": "https://api.github.com/repos/wycats/merb-core",
    "forks_url": "https://api.github.com/repos/wycats/merb-core/forks",
    "keys_url": "https://api.github.com/repos/wycats/merb-core/keys{/key_id}",
    "collaborators_url": "https://api.github.com/repos/wycats/merb-core/collaborators{/collaborator}",
    "teams_url": "https://api.github.com/repos/wycats/merb-core/teams",
    "hooks_url": "https://api.github.com/repos/wycats/merb-core/hooks",
    "issue_events_url": "https://api.github.com/repos/wycats/merb-core/issues/events{/number}",
    "events_url": "https://api.github.com/repos/wycats/merb-core/events",
    "assignees_url": "https://api.github.com/repos/wycats/merb-core/assignees{/user}",
    "branches_url": "https://api.github.com/repos/wycats/merb-core/branches{/branch}",
    "tags_url": "https://api.github.com/repos/wycats/merb-core/tags",
    "blobs_url": "https://api.github.com/repos/wycats/merb-core/git/blobs{/sha}",
    "git_tags_url": "https://api.github.com/repos/wycats/merb-core/git/tags{/sha}",
    "git_refs_url": "https://api.github.com/repos/wycats/merb-core/git/refs{/sha}",
    "trees_url": "https://api.github.com/repos/wycats/merb-core/git/trees{/sha}",
    "statuses_url": "https://api.github.com/repos/wycats/merb-core/statuses/{sha}",
    "languages_url": "https://api.github.com/repos/wycats/merb-core/languages",
    "stargazers_url": "https://api.github.com/repos/wycats/merb-core/stargazers",
    "contributors_url": "https://api.github.com/repos/wycats/merb-core/contributors",
    "subscribers_url": "https://api.github.com/repos/wycats/merb-core/subscribers",
    "subscription_url": "https://api.github.com/repos/wycats/merb-core/subscription",
    "commits_url": "https://api.github.com/repos/wycats/merb-core/commits{/sha}",
    "git_commits_url": "https://api.github.com/repos/wycats/merb-core/git/commits{/sha}",
    "comments_url": "https://api.github.com/repos/wycats/merb-core/comments{/number}",
    "issue_comment_url": "https://api.github.com/repos/wycats/merb-core/issues/comments/{number}",
    "contents_url": "https://api.github.com/repos/wycats/merb-core/contents/{+path}",
    "compare_url": "https://api.github.com/repos/wycats/merb-core/compare/{base}...{head}",
    "merges_url": "https://api.github.com/repos/wycats/merb-core/merges",
    "archive_url": "https://api.github.com/repos/wycats/merb-core/{archive_format}{/ref}",
    "downloads_url": "https://api.github.com/repos/wycats/merb-core/downloads",
    "issues_url": "https://api.github.com/repos/wycats/merb-core/issues{/number}",
    "pulls_url": "https://api.github.com/repos/wycats/merb-core/pulls{/number}",
    "milestones_url": "https://api.github.com/repos/wycats/merb-core/milestones{/number}",
    "notifications_url": "https://api.github.com/repos/wycats/merb-core/notifications{?since,all,participating}",
    "labels_url": "https://api.github.com/repos/wycats/merb-core/labels{/name}",
    "releases_url": "https://api.github.com/repos/wycats/merb-core/releases{/id}"
  }
]
```

As you can see we have quite a lot of data on each repo. 

## Instructions

  1. Finish the `FISGithubRepository` object. It should have the following properties and an `isEqual` method that compares the two `FISGithubRepository` objects.

  ```
  (NSString *)fullNamepa
  (NSURL *)htmlURL
  (NSString *)repositoryID
  ```

  2. In the `FISGithubAPIClient` create a method that retreives a list of all of the repositories, and passes the `NSArray` of `NSDictionaries` to a completionBlock
  3. Create a new method in `FISGithubRepository` that will take the `NSDictionary` representation of the repository and returns a new instance of `FISGithubRepository` all filled out.
  4. Add a method to `FISGithubDataStore` that uses `FISGithubAPIClient` to fill the `repositories` property with `FISGithubRepository` objects. In the completionBlock just pass back a `BOOL` success variable.
  5. In your `FISReposTableViewController` on `viewDidLoad` retreive the repos from the `FISGithubDataStore` and display them!
