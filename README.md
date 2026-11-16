# College Department Website (CSE Department)

CSE Department Website developed using HTML and CSS with Git branching, merging, and collaborative version control operations. (Assignment-04)

## Project Overview

A simple multi-page website for the Computer Science and Engineering (CSE) department. It has a home page, a contact page and a faculty page, all styled with a single shared stylesheet. The project was used to practise a Git feature-branch workflow: creating branches, committing, pushing to GitHub, merging into `main`, and resolving a real merge conflict.

## Technologies Used

- HTML5
- CSS3
- Git (Git Bash on Windows)
- GitHub
- Visual Studio Code (Live Server extension for local testing)

## Project Folder Structure

```
college-department-website/
├── index.html     # Home page
├── contact.html   # Contact Us page
├── faculty.html   # Our Faculty page
├── style.css      # Shared styles
└── README.md      # Project documentation
```

## Website Pages

| Page | File | Content |
|---|---|---|
| Home | `index.html` | Heading "Welcome to the CSE Department", sub-heading, welcome message, navigation links to Contact Us and Our Faculty |
| Contact Us | `contact.html` | "Contact the CSE Department": Department, Email (cse@college.edu), Phone (9876543210), Address (College Campus, Telangana), Home link |
| Our Faculty | `faculty.html` | "Faculty Members" table with Name, Designation and Specialization, Home link |

Faculty table:

| Name | Designation | Specialization |
|---|---|---|
| Dr. Rajesh | Professor | Artificial Intelligence |
| Dr. Priya | Associate Professor | Data Science |
| Dr. Kumar | Assistant Professor | Cyber Security |

## Git Workflow

### 1. Git initialization and first push

```bash
git init
git status
git add .
git commit -m "Initial commit - CSE Department Website"
git branch -M main
git remote add origin https://github.com/lovelithK/college-department-website.git
git remote -v
git push -u origin main
```

### 2. Feature branches, commits and pushes

| Branch | Change | Commit message |
|---|---|---|
| `feature/home` | Home page heading "Welcome to the CSE Department", tagline, navigation | Add department home page |
| `feature/contact` | New `contact.html` with department contact details | Add contact page |
| `feature/faculty` | New `faculty.html` with the faculty table | Add faculty page |
| `feature/home-update` | Home sub-heading "Department of Computer Science and Engineering" | Update home page heading |
| `feature/home-design` | Styled welcome message "Learn. Innovate. Excel." plus a `.highlight` style | Enhance home page design |

Commands used for each branch (example for `feature/contact`):

```bash
git checkout main
git pull origin main
git checkout -b feature/contact
git add contact.html
git commit -m "Add contact page"
git push -u origin feature/contact
```

### 3. Merging into main

```bash
git checkout main
git pull origin main
git status                       # working tree clean
git merge feature/home           # fast-forward
git merge feature/contact -m "Merge branch 'feature/contact' into main"
git merge feature/faculty -m "Merge branch 'feature/faculty' into main"
git push origin main

git merge feature/home-update    # fast-forward
git push origin main
git merge feature/home-design    # CONFLICT in index.html
```

### 4. Merge conflict demonstration and resolution

`feature/home-update` and `feature/home-design` were both created from the same commit of `main`, and both changed the same line of `index.html` (the line under the main heading). After `feature/home-update` was merged, merging `feature/home-design` stopped with:

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

The conflicting section looked like this:

```html
<<<<<<< HEAD
  <h2 class="tagline">Department of Computer Science and Engineering</h2>
=======
  <p class="tagline highlight">Learn. Innovate. Excel.</p>
>>>>>>> feature/home-design
```

Resolution: `index.html` was edited to keep both changes (the sub-heading from `feature/home-update` and the styled welcome message from `feature/home-design`), the "Welcome to the CSE Department" heading was kept, and all conflict markers were removed:

```html
  <h1>Welcome to the CSE Department</h1>
  <h2 class="tagline">Department of Computer Science and Engineering</h2>
  <p class="tagline highlight">Learn. Innovate. Excel.</p>
```

Then the merge was completed and pushed:

```bash
git add index.html
git commit -m "Resolve merge conflict in home page"
git push origin main
```

All feature branches were kept (not deleted) to show the workflow.

### 5. Verification

```bash
git status
git branch
git branch -a
git log --oneline
git log --graph --oneline --all
git remote -v
```

## Running the Website

1. Open the `college-department-website` folder in Visual Studio Code.
2. Click **Go Live** (Live Server extension) in the status bar, or open `index.html` in a browser.
3. The site opens at `http://127.0.0.1:5500/index.html`. Use the links to visit Contact Us and Our Faculty.

## Repository

https://github.com/lovelithK/college-department-website
