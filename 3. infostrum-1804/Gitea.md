# Gitea
## Information
- The Gitea server is running on `x.x.x.x` which is a `CentOS/Linux` OS sytstem, and we use `Docker` to run a container with Gitea image, then host the web server.
- The location and the file structure is:

```
/var/lib/gitea/
               git/
                   repositories/
                               ...
               gitea/
                     conf/
                     gitea.db
                     log/
                     ...
               ssh/
                   {some keys...}
```
## Set-ups
- Download the latest version of Gitea `image` with `docker pull` command.

```docker
docker pull gitea/gitea:latest
```

- Make a directory for Gitea.
  - This directory will exist if you have already built once.

```docker
sudo mkdir -p /var/lib/gitea
```

- Start Docker to run the container, and this container is derived from Gitea image. 
  - `A container is a process which runs on a host.`

```docker
docker run -d --name=gitea -p 10022:22 -p 10080:3000 -v /var/lib/gitea:/data gitea/gitea:latest
```

- The parameters in this command:
  - `-d` = `detach` means that it'll run the container in the background (it's often used!)
  - `--name=[Container Name]`
  - `-p` `[outside-port]:[inside-port]` = `port exposing` means that expose ports inside the container to the outside one.
  - `-v` `[outside-dir]:[inside-dir]` = `volume setting` means that the directory outside the container is shared with inside one.

## Gitea Characters
### Users
#### Settings
- Profile
  - **Username**, Full Name, **Email Address**, Website, Location, Language and Avatar
- Account
  - **Password**, Alternative Email and Delete Account
- Security
  - Two-Factor Authentication, OpenID
- Applications
  - Access Tokens
- SSH / GPG Keys
  - SSH Keys, GPG Keys
- Organizations
- Repositories

### Repositories
#### Settings
  - Repository
    - **Repository Name**, Visibility, Description, Website
    - Advanced
      - Wiki: Built-In, External
      - Issues: Built-In, External
      - PR settings
    - Enable git fsck
    - Transfer, Delete Wiki and Repository
  - Collaborators
    - Add and Change Permission
  - Branches
    - Branch Protection: Push, Merge
  - Webhooks
  - Git Hooks
  - Deploy Keys

### Teams
#### Settings
  - **Team Name**, Description

### Organizations
#### Settings
  - Organization
    - **Organization Name**, Organization Full Name, Description, Website, Location, Maximal Number of Repositories and Avatar
  - Webhooks
  - Delete Organization

## Relationship
### 1. Everyone has their own repositories

```
UserA - RepoA-1
      - RepoA-2

UserB - RepoB

UserC - RepoC-1
      - RepoC-2
      - RepoC-3
```

### 2. There might be some Collaborative Repositories

> After you create Organization, system create a Team called `Owners` and you will be in there.

```
OrganizationA - RepoBigA
              - Owners Team(default) - UserA
                                     - UserB
```

> Add `RepoBigA` to `Owners Team`, then the users in the `Owners Team` can start to collaborate

```
OrganizationA - RepoBigA
              - Owners Team - RepoBigA
                            - UserA
                            - UserB
```

### All of the above

```
WebApp - WebA Repo
       - WebB Repo
       - WebC Repo
       - Owners Team - WebA Repo
                     - WebB Repo
                     - WebC Repo
                     - UserA - RepoA
       - Frontend Team - UserB - RepoB
       - Backend Team - UserC - RepoC
```

> Assume `RepoWebA` is on production, and it no need to develop for now
> and `RepoWebB` is static web, and there is no need for backend
> and `RepoWebC` is full-side web application.

```
WebApp Organization - WebA Repo
                    - WebB Repo
                    - WebC Repo
                    - Owners Team - WebA Repo
                                  - WebB Repo
                                  - WebC Repo
                                  - UserA - RepoA
                    - Frontend Team - WebB Repo
                                    - WebC Repo
                                    - UserB - RepoB
                    - Backend Team - WebC Repo
                                   - User C - RepoC
```

### Summary
- Organization 
  - Team
  - Repository
- Team
  - User
  - Repository
- User
  - Repository
