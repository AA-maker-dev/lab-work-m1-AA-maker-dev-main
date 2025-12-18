# Title: **Basic Introduction to Discord and GitHub**

##  **Objectives**

1. **Understand and create** a Discord account & server
2. **Explore GitHub**, repositories, commits, branches, and issues
3. **Connect Discord with GitHub** using webhooks
4. Learn how version control and communication tools help in **team collaboration**

---

#  **Background Theory**

---

#  **1. What is Discord? – Background Theory**

Discord is a **communication platform** designed for community building. It supports **text, voice, and video** channels, making it popular among developers, gamers, and project teams.

###  **Key Features of Discord**

| Feature      | Description                                |
| ------------ | ------------------------------------------ |
| **Servers**  | Community spaces with channels             |
| **Channels** | Text/voice rooms inside a server           |
| **Roles**    | Permissions like admin, mod, member        |
| **Bots**     | Automated helpers (music bots, moderation) |
| **Webhooks** | Connect external apps like GitHub          |

###  **Why Discord in Development Teams?**

* Real-time communication
* Organizing discussions into channels
* Integrations with GitHub, Trello, etc.
* Useful for standups, announcements, Q/A

---

#  **2. What is GitHub? – Background Theory**

GitHub is a **cloud-based version control platform** built on **Git**. It is used for storing code, tracking changes, and collaborating on projects.

###  **Key Concepts**

| Term             | Meaning                         |
| ---------------- | ------------------------------- |
| **Repository**   | Folder/project hosted on GitHub |
| **Commit**       | Saved changes with a message    |
| **Branch**       | A separate line of development  |
| **Pull Request** | Request to merge code changes   |
| **Issues**       | Bug reports or feature requests |

###  Why Developers Use GitHub

* Works with **Git**, the industry-standard VCS
* Collaboration with teams
* Tracks every change
* Automates workflows through **GitHub Actions**
* Hosts open-source projects

---

#  **3. Discord–GitHub Integration**

Discord allows GitHub to send **notifications** to your server using **webhooks**.
Examples:

* New commit pushed
* New pull request
* Issue opened
* Release published

###  **Webhook Flow**

```
GitHub Repository → Webhook → Discord Channel
```

###  **Example: Creating a GitHub Webhook for Discord**

1. Create a Discord server
2. Go to **Server Settings → Integrations → Webhooks**
3. Create a webhook and copy its URL
4. Go to your GitHub repo → Settings → Webhooks
5. Paste the URL
6. Select events (push, PR, issues)
7. Save!

---

#  **Procedure**

```
1. Install and set up Discord (PC/mobile)
2. Create a new server and add channels
3. Create roles (Admin, Member, Developer)
4. Create a GitHub account
5. Create a new repository
6. Make a README, commit files, create branches
7. Explore pull requests and issues
8. Connect GitHub repo to Discord using a webhook
9. Test integration by pushing a commit
10. Observe Discord notifications from GitHub
```

---

#  **Output**

 **Discord Server Setup**

* Channels created
* Roles assigned
* Webhook integrated

 **GitHub Activities**

* Repository created
* Commits made
* Branches merged
* Issues tracked
* Discord received notifications

---

#  **Conclusion**

This lab introduces how Discord and GitHub support communication and version control in modern software development.
Discord enhances **team coordination**, while GitHub ensures **structured code management**.
By integrating both, teams can collaborate efficiently, track updates instantly, and maintain organized workflows in any project.

---
