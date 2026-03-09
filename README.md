# SpellQuiz — User-Facing Feature Inventory

> Complete inventory of every user-facing feature, organized by user role.
> Intended for use in onboarding design, lifecycle email planning, and product documentation.
> Last updated: March 2026

---

## Key Product Value Pillars

The core learning outcomes the platform delivers to its users:

- **Spelling mastery** — Interactive quizzes, adaptive difficulty, and practice modes that track mastered and missed words over time
- **Vocabulary building** — Grade-leveled word banks, vocabulary tests, and targeted exercises across K–12 content
- **Reading comprehension** — Graded reading passages with timed comprehension questions and progress tracking
- **Competitive learning** — Live multiplayer Spelling Bee competitions and five championship leaderboards that motivate through comparison
- **Structured learning** — Courses and lessons with sequential, multi-format exercises and saved progress
- **Guided learning with assignments** — Teachers and parents can assign spelling exams and training lists, set time limits and attempt counts, and track every student's results in detail

---

## How to read this document

Features are organized into two types of sections:

**Role-Specific Features (§1–5)**
1. **Universal** — available to everyone, including unauthenticated guests
2. **Teacher** — classroom management, content creation, assignment, and student reporting
3. **Parent** — child monitoring, assignment, and family subscription management
4. **Self-learner** — independent learning, progress tracking, and personal billing
5. **Student** — assigned work, self-directed learning, and progress tracking

**Shared Learning Features (§6)**
Learning features available to all authenticated roles (Teacher, Parent, Self-learner, Student) are listed once in §6 to avoid repetition across role sections. These include all spelling modes, reading, vocabulary, courses, Spelling Bee, championships, and more.

Sections 2–5 inherit all features from §1, and all authenticated roles in §2–5 also have access to everything in §6.

---

## Important spelling feature distinctions

The product has six separate spelling-related features that are often confused:

| Feature | Route | What it is |
|---------|-------|-----------|
| **Spelling Test** | `/spelling-test/` | Grade and topic browser — select what to test, then launch the quiz engine |
| **Spelling Quiz** | `/spelling-quiz/` | The interactive quiz engine — type answers word by word with audio |
| **Spelling Practice** | `/spelling-practice/` | A separate self-paced practice system with its own road progression and data model |
| **Spelling Practice Quiz** | `/spelling-practice-quiz/` | The quiz player for the practice system (express and step-by-step modes) |
| **Spelling Training** | `/spelling-training/` | Teacher-created custom word lists with audio, assigned to students |
| **Spelling Training Quiz** | `/spelling-training-quiz/` | The quiz player for assigned training lists |

These share no data models and serve distinct purposes.

---

## 1. Universal Features
*Available to all users, including guests (unauthenticated).*

### Marketing and Discovery

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Home page** | Browse product overview, read feature highlights and testimonials, navigate to register or log in | `/` |
| **Features page** | Read a detailed breakdown of product capabilities | `/features` |
| **Pricing page** | Compare subscription plans by role (Teacher, Parent, Self-learner); see monthly vs. yearly costs and free trial details | `/pricing` |
| **Testimonials** | Read reviews from other users | `/testimonials` |
| **FAQ** | Browse frequently asked questions and answers | `/faq` |
| **Contact form** | Submit a support request or feedback message | `/contacts` |
| **Blog** | Read spelling tips, educational articles, and graded content | `/blog`, `/blog/[slug]` |
| **Video library** | Browse and watch educational videos organized by category | `/videos` |
| **Idioms** | Browse the idiom library index | `/idioms` |
| **Idiom detail** | Read the definition, usage, and examples for a specific idiom | `/idiom/[slug]` |
| **Terms of service** | Read the terms of use | `/terms` |
| **Privacy policy** | Read the privacy policy | `/policy` |

### Authentication

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Register** | Choose role (self-learner, parent, or teacher), complete age gate if self-learner (>16 required), create account | `/auth/register` |
| **Adult login** | Sign in with email and password | `/auth/login` |
| **Student login** | Enter teacher's email, pick name from class roster, enter password | `/auth/student` |
| **Forgot password** | Request a password reset link by email | `/auth/forgot` |
| **Email verification** | Verify email address after registration | `/verification` |
| **SSO — Google** | Sign in or register with a Google account | `/auth/google` |
| **SSO — Facebook** | Sign in or register with a Facebook account | `/auth/fb` |
| **SSO — Clever** | Sign in via Clever (for school-connected teachers and students) | `/auth/clever` |
| **SSO — ClassLink** | Sign in via ClassLink (for school-connected teachers and students) | `/classlink` |

### Public Learning Content

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Word bank (browse)** | Browse K–12 graded word lists with audio pronunciation; accessible without login | `/words` |
| **Spelling Bee word lists (browse)** | Browse curated Spelling Bee competition word lists by grade | `/spelling-bee-words` |
| **Reading comprehension — Grade 1** | Read a Grade 1 passage and answer comprehension questions; guests are limited to Grade 1 only | `/reading-comprehension` |
| **Fun quizzes (browse)** | View the fun quiz catalog by category without logging in | `/quizzes` |
| **Course catalog (browse)** | Browse available courses without enrolling | `/courses` |
| **Spelling Bee Online (observe/guest)** | View the active player lobby; enter a name and join a game without a persistent account — no stats saved | `/spelling-bee-online` |

---

## 2. Teacher Features
*Teachers self-register. They create classes, manage students, produce content, and assign work.*

### Dashboard

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Teacher dashboard** | See summary stats (students, classes, quizzes assigned, content created); quick-launch links to all features; activity block for own learning | `/school/dashboard` |

### Classroom Management

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Create a class** | Create a named class with language and description; get a shareable student enrollment link | `/school/classes` |
| **Edit a class** | Rename a class, change its language or description | `/school/classes` |
| **Delete a class** | Remove a class | `/school/classes` |
| **Create student accounts** | Add individual students with name, password, and language; assign to a class | `/school/classes` |
| **Edit student accounts** | Update a student's name, password, language, or class assignment | `/school/classes` |
| **Delete students** | Remove a student account (cascades through quiz and training data) | `/school/classes`, `/school/students` |
| **Bulk import students (CSV)** | Upload a CSV file to create multiple students at once | `/school/students` |
| **Export students (CSV)** | Download a CSV of all students | `/school/students` |
| **Manage students list** | Search, filter, and sort all students by name, class, or subscription status | `/school/students` |
| **Invite parents** | Send a parent invitation email to link a parent to a specific student | `/school/students` |
| **Manage parent requests** | Approve or decline incoming parent connection requests | `/school/dashboard` |
| **Clever roster sync** | Pull class rosters from Clever; auto-create student accounts from school data | `/school/dashboard` |
| **ClassLink roster sync** | Pull class rosters from ClassLink | `/school/dashboard` |

### Content Creation

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Spelling content editor** | Create spelling words with audio (record microphone or upload file), assign to grade and topic, deploy instantly to the spelling quiz | `/school/editor` |
| **Spelling content library** | Browse, search, filter, and manage all created spelling content; filter by grade, topic, language, and content owner | `/school/content` |
| **Spelling sentences editor** | Create sentence-level spelling content with recorded audio for use in spelling practice mode | `/school/seditor` |
| **Spelling sentences library** | Browse and manage created spelling sentence lists | `/school/sentences` |
| **Spelling training list creator** | Build custom word lists with audio in 10 languages (US, UK, CA, AU English, French, German, Italian, Spanish, Portuguese, Other) and publish them for students | `/spelling-training/editor`, `/spelling-training/lists` |
| **Spelling training word library** | Browse, search, and listen to all available training words; filter by language | `/spelling-training/words` |
| **Course creator** | Create a course with title, description, and thumbnail; publish or save as draft | `/lessons/courses/editor`, `/lessons/courses/list` |
| **Lesson builder** | Add sequential lessons to a course; build exercises (audio, image choice, missing word, word ordering, sentence correction, matching, YouTube task, reading) | `/lessons/lessons/editor` |
| **Worksheet creator** | Build printable and interactive worksheets with exercises; publish or keep as draft (requires an author profile) | `/worksheets/editor`, `/worksheets/list` |

### Assignment

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Assign spelling exams** | Select content by grade, topic, and language; choose individual students or a whole class; set a due date, time limit, and maximum attempt count | `/school/assign` |
| **Assign spelling training lists** | Assign a custom training list to individual students or a class | `/spelling-training/assignments` |
| **Assignments dashboard** | See all created exams and work assignments with status (assigned / in-progress / completed), score, student name, and creation date | `/school/assignments` |
| **Delete an assignment** | Remove an exam assignment before or after completion | `/school/assignments` |

### Reporting (Teacher's Students)

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Performance report** | View all students' quiz performance filtered by date range, grade, topic, quiz type, and class; sortable table with score, words mastered, words missed, and time spent | `/reports/performance` |
| **Spelling report** | See per-grade spelling performance across all managed students | `/reports/spelling` |
| **Quiz log** | Browse the full quiz attempt history for any student with score and timestamp | `/reports/quiz-log` |
| **Quiz statistics** | View aggregated quiz stats (average score, attempt count, type breakdowns) | `/reports/quiz-stats` |
| **Spelling words report** | See which words each student has mastered or missed | `/reports/spelling-words` |
| **Practice words report** | View word-level performance from spelling practice sessions | `/reports/practice-words` |
| **SBO words report** | View words mastered by students in Spelling Bee Online mode | `/reports/sbo-words` |
| **Words statistics** | See vocabulary acquisition over time per student | `/reports/words-statistics` |
| **Readings report** | View reading comprehension performance per student | `/reports/readings` |
| **Training assignments report** | See completion progress, score, and date for each training list assigned to students | `/spelling-training/assignments` |
| **Lesson assignments report** | View student progress through course lessons | `/lessons/lessons/assignments` |

### Billing and Account

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Subscribe** | Purchase a monthly or yearly Teacher plan; enter a coupon code | `/payment/plan`, `/payment/subscribe` |
| **Subscription management** | View current plan, see and manage licensed students, add or remove students from the subscription | `/profile` (subscription tab) |
| **Subscription history** | View all past and current subscriptions | `/payment/history` |
| **Subscription detail** | View full payment history, license breakdown, and status for any subscription | `/payment/sub-detail` |
| **Cancel subscription** | Cancel recurring PayPal billing | `/profile` (subscription tab) |
| **User profile** | Update name, email, avatar, country, and timezone | `/profile` |
| **View own certificates** | See spelling achievement certificates earned personally | `/certificates` |

---

## 3. Parent Features
*Parents self-register (or are invited). They monitor children, assign work, and manage a family subscription.*

### Dashboard

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Parent dashboard** | See an overview of all linked students, recent quiz activity per student, and quick-launch links to own learning | `/parent/dashboard` |

### Student Management

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Create student accounts** | Add a child as a student with name, password, and language | `/school/classes` |
| **Edit student accounts** | Update a child's name, password, or class assignment | `/school/classes` |
| **Delete students** | Remove a student account | `/school/classes`, `/school/students` |
| **Link to a teacher's class** | Enroll a child in a teacher's class via invitation link or email code | `/school/classes` |
| **View student activity** | See recent quiz attempts and practice history for each linked child | `/parent/dashboard` |

### Assignment

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Assign spelling exams** | Create and assign a timed spelling exam to a child (same flow as teacher) | `/school/assign` |
| **Assign spelling training lists** | Assign a training word list to a child | `/spelling-training/assignments` |
| **Assignments dashboard** | See all created assignments with status, score, and progress per child | `/school/assignments` |

### Reporting (Parent's Children)

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Performance report** | View a child's quiz performance filtered by date range, grade, topic, and quiz type | `/reports/performance` |
| **Spelling report** | See per-grade spelling performance for each child | `/reports/spelling` |
| **Quiz log** | Browse a child's full quiz attempt history | `/reports/quiz-log` |
| **Quiz statistics** | View quiz stats for a child | `/reports/quiz-stats` |
| **Spelling words report** | See mastered and missed words per child | `/reports/spelling-words` |
| **Practice words report** | View word-level practice performance for a child | `/reports/practice-words` |
| **SBO words report** | View SBO words mastered by each child | `/reports/sbo-words` |
| **Words statistics** | See vocabulary growth over time per child | `/reports/words-statistics` |
| **Readings report** | View reading comprehension results per child | `/reports/readings` |
| **Training assignments report** | See completion and score for each training list assigned to children | `/spelling-training/assignments` |
| **View children's certificates** | View certificates earned by each linked child | `/certificates` |

### Billing and Account

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Subscribe** | Purchase a monthly or yearly Parent plan | `/payment/plan`, `/payment/subscribe` |
| **Subscription management** | View current plan, manage licensed students | `/profile` (subscription tab) |
| **Subscription history** | View all past and current subscriptions | `/payment/history` |
| **Subscription detail** | View full payment and license history | `/payment/sub-detail` |
| **Cancel subscription** | Cancel recurring billing | `/profile` (subscription tab) |
| **User profile** | Update name, email, avatar, country, and timezone | `/profile` |
| **View own certificates** | See own spelling achievement certificates | `/certificates` |

---

## 4. Self-Learner Features
*Self-learners are adults (age >16) who register independently. A free trial is created automatically at signup. They are never assigned work by another user.*

### Dashboard

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Self-learner dashboard** | See personal activity summary and quick-launch buttons to all learning modes | `/student/dashboard` |

### Progress Tracking

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **My practice view** | See all personal quiz attempts with score, progress percentage, and status | `/student/practice` |
| **Quiz log** | Browse complete personal quiz attempt history with scores and timestamps | `/reports/quiz-log` |
| **Quiz statistics** | View aggregated personal quiz stats | `/reports/quiz-stats` |
| **Spelling report** | See personal per-grade spelling performance | `/reports/spelling` |
| **Spelling words report** | View which words have been personally mastered vs. missed | `/reports/spelling-words` |
| **Practice words report** | View word-level performance from practice sessions | `/reports/practice-words` |
| **SBO words report** | View words mastered in Spelling Bee Online mode | `/reports/sbo-words` |
| **Words statistics** | See vocabulary acquisition over time | `/reports/words-statistics` |
| **Readings report** | View reading comprehension performance | `/reports/readings` |
| **Championship leaderboards** | See personal ranking across all 5 leaderboards: Spelling, Vocabulary, SBO, Adaptive, Practice | `/championship` |
| **Certificates** | Earn and view spelling achievement certificates | `/certificates`, `/certificate` |

### Billing and Account

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Free trial** | Automatically created at registration; provides time-limited full access to premium features | Auto-created |
| **Subscribe** | Purchase a monthly or yearly Self-learner plan after the trial expires | `/payment/plan`, `/payment/subscribe` |
| **Subscription management** | View current plan and status | `/profile` (subscription tab) |
| **Subscription history** | View all past subscriptions | `/payment/history` |
| **Cancel subscription** | Cancel recurring billing | `/profile` (subscription tab) |
| **User profile** | Update name, email, avatar, country, and timezone | `/profile` |

---

## 5. Student Features
*Students are created by a teacher or parent — they never self-register. They complete assigned work and can also use self-directed learning modes.*

### Assigned Work

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Student dashboard** | See activity shortcuts for all learning modes and any pending assigned work | `/student/dashboard` |
| **Complete spelling exams** | Take teacher- or parent-assigned spelling exams; subject to time limits, attempt count limits, and due dates | `/spelling-quiz` |
| **Complete spelling training assignments** | Work through assigned word lists with audio; track progress percentage per list | `/spelling-training`, `/spelling-training-quiz` |
| **My assignments view** | See all assigned exams and practice work with status (assigned / in-progress / completed), score, and progress | `/student/practice` |

### Progress Tracking

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **My practice view** | See all personal quiz attempts (two tabs: Practices and Exams) | `/student/practice` |
| **Quiz log** | Browse full personal quiz attempt history | `/reports/quiz-log` |
| **Quiz statistics** | View aggregated personal quiz stats | `/reports/quiz-stats` |
| **Spelling report** | See per-grade spelling performance | `/reports/spelling` |
| **Spelling words report** | View mastered vs. missed words | `/reports/spelling-words` |
| **Practice words report** | View word-level practice performance | `/reports/practice-words` |
| **SBO words report** | View words mastered in Spelling Bee Online | `/reports/sbo-words` |
| **Words statistics** | See vocabulary progress over time | `/reports/words-statistics` |
| **Readings report** | View reading comprehension results | `/reports/readings` |
| **Championship leaderboards** | See personal standing across 5 leaderboards | `/championship` |
| **Certificates** | Earn and view spelling achievement certificates | `/certificates`, `/certificate` |

### Account

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Link a parent** | Enter a parent's email to send a connection request; parent approves and gains monitoring access | `/student/parents` |
| **User profile** | Update name, avatar, and password | `/profile` |

---

## 6. Shared Learning Features
*Available to all authenticated users — teachers, parents, self-learners, and students. Listed once here to avoid repetition across role sections §2–5.*

---

### Spelling

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Spelling Test** | Browse spelling content by K–12 grade and topic; see the current grade's best speller and earned cups; launch the spelling quiz from the selected topic | `/spelling-test` |
| **Spelling Quiz** | Take an interactive word-by-word spelling quiz; hear audio pronunciation; type answers; track score, mastered words, and mistakes in real time; quiz advances automatically; sends report to parent email on exam completion | `/spelling-quiz` |
| **Spelling Practice hub** | View a visual "practice road" showing milestone progress (words mastered in steps of 10); see current mastered word count; launch the practice quiz | `/spelling-practice` |
| **Spelling Practice Quiz** | Take a practice quiz in Express mode (fast input) or Step-by-step mode (audio-guided); view results with master / no-master word breakdown after each session | `/spelling-practice-quiz` |
| **Spelling Training hub** | Browse available training lists (teacher-created or self-created where applicable); see progress on assigned lists; start or continue a list | `/spelling-training` |
| **Spelling Training Quiz** | Work through a training list word by word with audio; complete the list to mark as done | `/spelling-training-quiz` |
| **Adaptive Spelling** | Follow a personalized difficulty road that adjusts automatically based on word mastery; visual milestone map shows current level and next targets; auto-advances level when mastery threshold is reached | `/adaptive-spelling` |

---

### Spelling Bee Online

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Spelling Bee Online lobby** | View active players (with avatars, countries, and levels); see own SBO level and mastered word count; create or join a game room | `/spelling-bee-online` |
| **Spelling Bee game** | Compete in a live multiplayer spelling challenge; hear audio of words; type answers in real time against other players; track health/lives; advance through game levels | `/spelling-bee-game` |

---

### Vocabulary

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Vocabulary Test** | Take a vocabulary quiz (requires active subscription for full access); view the best vocabulary leaderboard | `/vocabulary-test` |
| **Word bank** | Browse K–12 graded spelling and vocabulary word lists; listen to audio pronunciation for each word; switch between Spelling Words and Spelling Bee Words tabs | `/words` |
| **Spelling Bee word lists** | Browse curated Spelling Bee competition word lists by grade with audio | `/spelling-bee-words` |

---

### Reading

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Reading comprehension hub** | Select a grade level; browse reading passages available for that grade | `/reading-comprehension` |
| **Reading passage** | Read a graded passage (text with optional image); timer counts down to set a minimum reading time before questions begin | `/reading-test/[slug]` |
| **Reading questions** | Answer comprehension questions after reading the passage; questions advance automatically; completion redirects to results | `/reading-test/[slug]` (question mode) |

---

### Courses and Lessons

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Course catalog** | Browse all published courses with title, thumbnail, and description | `/courses` |
| **Course overview** | View lessons within a course; see progress through the course | `/lessons/courses/item` |
| **Lesson player** | Work through a lesson step by step; exercises include audio, image choice, missing word, word ordering, sentence correction, matching, and YouTube tasks; progress is saved after each step | `/lessons/lessons/item` |
| **Lesson results** | View score, time spent, and exercise outcomes after completing a lesson | `/lessons/lessons/results` |

---

### Fun Quizzes

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Fun quiz catalog** | Browse gamified quizzes by category; view thumbnails and descriptions | `/quizzes` |
| **Play a fun quiz** | Answer image-choice or word-choice questions in a game format | `/quizzes/[slug]` |
| **Fun quiz stats** | View personal performance for a completed fun quiz | `/quizzes/statistic` |
| **Personal quiz stats** | View overall stats across all fun quizzes | `/quizzes/userstat` |

---

### Worksheets

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Worksheet player** | Complete an interactive worksheet; submit answers; view score | `/worksheets/item` |

---

### Idioms

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Idiom library** | Browse the full idiom collection | `/idioms` |
| **Idiom detail** | Read the meaning, origin, and usage examples of a specific idiom | `/idiom/[slug]` |

---

### Championships

| Feature | What the user can do | Route |
|---------|---------------------|-------|
| **Spelling leaderboard** | See the top spellers by mastered word count; view own rank | `/championship` |
| **Vocabulary leaderboard** | See the top vocabulary performers by best quiz score | `/championship` |
| **Spelling Bee Online leaderboard** | See the top SBO players | `/championship` |
| **Adaptive leaderboard** | See the top adaptive spelling performers | `/championship` |
| **Practice leaderboard** | See the top spelling practice performers | `/championship` |

---

## Feature Access Matrix

| Feature area | Guest | Student | Self-Learner | Parent | Teacher |
|-------------|:-----:|:-------:|:------------:|:------:|:-------:|
| Spelling Test (browser) | — | ✓ | ✓ | ✓ | ✓ |
| Spelling Quiz (engine) | — | ✓ | ✓ | ✓ | ✓ |
| Spelling Practice | — | ✓ | ✓ | ✓ | ✓ |
| Spelling Training (take) | — | ✓ | ✓ | ✓ | ✓ |
| Spelling Training (create/assign) | — | — | — | ✓ | ✓ |
| Spelling content creation | — | — | — | — | ✓ |
| Adaptive Spelling | — | ✓ | ✓ | ✓ | ✓ |
| Spelling Bee Online (guest) | ✓ (no stats) | ✓ | ✓ | ✓ | ✓ |
| Vocabulary Test | — | ✓ | ✓ (sub req.) | ✓ | ✓ |
| Word bank | ✓ | ✓ | ✓ | ✓ | ✓ |
| Reading (Grade 1 only for guests) | Grade 1 | ✓ | ✓ | ✓ | ✓ |
| Fun quizzes | Browse only | ✓ | ✓ | ✓ | ✓ |
| Courses (take) | Browse only | ✓ | ✓ | ✓ | ✓ |
| Courses (create) | — | — | — | — | ✓ |
| Worksheets (take) | — | ✓ | — | — | — |
| Worksheets (create) | — | — | — | — | ✓ |
| Idioms | ✓ | ✓ | ✓ | ✓ | ✓ |
| Exam assignment | — | — | — | ✓ | ✓ |
| Class management | — | — | — | ✓ | ✓ |
| Student management | — | — | — | ✓ | ✓ |
| Personal reports | — | ✓ | ✓ | ✓ (own) | ✓ (own) |
| Student/child reports | — | — | — | ✓ (children) | ✓ (students) |
| Championships | — | ✓ | ✓ | ✓ | ✓ |
| Certificates | — | ✓ | ✓ | ✓ | ✓ |
| Parent linking | — | ✓ | — | — | — |
| Subscription / billing | — | — | ✓ | ✓ | ✓ |
