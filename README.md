
----
Each engine is a **black box microservice** that:

- Has its own database/state
- Exposes clear APIs
- Can run independently for development
- Plugs into the main app via standardized interfaces

**Final Integration**: All 5 engines communicate through a central message bus and shared user identity service.

---
## Core Philosophy

**This is not a productivity tool. This is a ranked competitive league for SWE careers.**

- Ego is allowed.
- Status is earned through proof, not claims.
- Inactivity is death. Contribution is survival.
- The platform rewards grinders and purges lurkers.
---
# ENGINE 1: GRIND ENGINE 🧮

## Core Purpose

**The LC grinding tracking system. Monitors, validates, and scores all problem-solving activity.**

## What This Engine Does

### 1. LeetCode Session Management

**Session Types:**

- **Ranked Sessions** (affects rank, earns XP, full enforcement)
- **Casual Sessions** (practice only, no rank impact)

**Ranked Session Flow:**

```
START RANKED SESSION
↓
Pre-flight checks:
- LC account verified via OAuth
- No active sessions
- User not on probation
↓
Session initialized:
- Fullscreen lock enabled
- Tab tracking started
- Timer started
- Problem selection recorded
↓
DURING SESSION:
- Monitor: tab switches, time spent, attempts
- Detect: hints used, code similarity, copy-paste
- Track: solution quality, test cases passed
↓
SESSION END:
- Calculate XP based on performance
- Grade: S+, S, A, B, C, D, F
- Update pattern mastery
- Emit XP event → Rank Engine
- Emit activity event → Purge Engine
```

**Anti-Cheat During Session:**

- Tab switch detection (≥3 switches = session flagged)
- Code similarity analysis (compare to known solutions)
- Timing analysis (too fast for difficulty = suspicious)
- Pattern detection (copy-paste signatures)

### 2. Pattern Mastery System

**18 Core Patterns Tracked:**
[[Patterns]]

---
**Spectator Features:**

- Can chat with other spectators

**Privacy Controls:**

- User can disable spectators
- User can allow followers only
- User can make sessions public

### 8. Personal Bests & Records

**Tracked Records:**

- Fastest Easy solve
- Fastest Medium solve
- Fastest Hard solve
- Most problems in one session
- Longest session (time)
- Highest XP session
- Perfect week (7/7 days grinded)
- Perfect month (30/30 days grinded)

APIs exposed from this engine allow seamless interaction with other components. For instance, the **Rank Engine**receives XP updates whenever a user completes sessions, the **Purge Engine** logs activities for ROI calculations, and the **Social Engine** notifies the user’s network when a pattern is mastered. Hackathon deliverables include features like live session tracking, problem-of-the-day suggestions, replay systems, and advanced anti-cheat mechanisms, ensuring the system is both engaging and reliable.

---

# ENGINE 2: Career Engine

The **Career Engine** serves as an intelligence layer for tracking and managing a user’s job applications, interview processes, and career milestones. Its core goal is to aggregate pipeline data, verify offers, and provide insights for career decision-making. Users can manually log applications and interview stages, while an automated email integration system detects OA (Online Assessment) invites, interview schedules, and offer letters directly from the user’s inbox. This reduces manual effort and ensures the pipeline is accurate and up-to-date.

A standout feature is **War Rooms**, which are community-driven channels for each company. War Rooms provide real-time hiring intelligence, including verified timelines, interview difficulty ratings, OA waves, and recent activity feeds. Community verification ensures the information is trustworthy—events upvoted by multiple users can be broadcast nationally. Users can also log and search interview questions, creating a crowd-sourced, up-to-date database of questions with difficulty ratings, solution approaches, and recency alerts.

The engine also handles **offer management and verification**. Users can submit offers with details like compensation, bonuses, relocation, and start date. A combination of automated checks and manual moderation ensures offers are genuine, and verified offers are highlighted on the user profile. The system provides comparison tools against community and Levels.fyi data, helping users benchmark their offers against peers. XP is awarded for milestones like verified offers, referral contributions, or completing pipeline steps, gamifying the career tracking experience.

Finally, the **Timeline Prediction Engine** uses aggregated historical data to predict expected dates for OAs, phone screens, finals, and offers for each company and role. It provides users with real-time updates, including live tracking of OA waves and deadlines. The engine also supports referral tracking, milestone celebrations, and email intelligence, creating a comprehensive career management platform. APIs are exposed to update XP, log activities, and broadcast achievements to other systems, integrating gamification with career progress.

---

# ENGINE 3: SOCIAL ENGINE

## Core Purpose
**The community interaction layer. Feed, posts, comments, reactions, DMs, bounties, moderation.**

## What This Engine Does

### 1. Triple-Feed Architecture

**Three Feeds:**

**National Feed (The Main Stage)**
```
What shows here:
All verified offers
Top weekly performances (#1 grinder, etc.)
Purge announcements (weekly bloodbath)
Highly upvoted posts from any feed (≥200 upvotes)
Platform-wide announcements
FAANG/Top-tier company drops

Sort by: Recency, Hype (reactions), Impact

Example Posts:
─────
🏆 VERIFIED OFFER
@salman_goated → Amazon SDE Intern
Posted 2m ago
🔥 2.4k  🧠 891  🐐 445  😭 1.2k
[View Stats] [Compare Similar]
─────
💀 WEEKLY PURGE COMPLETE
847 accounts deleted | 1,203 on probation
Next purge: 6d 14h
─────
```

**School Feed (Your Circle)**
```
What shows here:
Posts from same school (.edu domain)
School-specific job drops (local companies recruiting)
School rankings movement
School-wide achievements
Study group activity

Filter: Your school only (umn.edu)

Example Posts:
─────
📍 UMN CS FEED
@jenny_umn: Emerson doing on-campus interviews at CSE Career Fair
↑ 67 (verified by community)
─────
🏫 UMN RANKINGS UPDATE
@mike_cs27 jumped #15 → #3 in school rank
─────
```

**Company Feed (War Rooms)**
```
What shows here:
✅ All activity related to specific company
✅ Timeline drops (OAs sending NOW)
✅ Interview questions logged
✅ Offers from that company
✅ Application tips
✅ Company-specific discussions

Filter: Select company (Meta, Google, Amazon, etc.)

Example Posts:
─────
LIVE DROP - META
@user1: OA invite just received (10:47am)
↑ 234 → Broadcast to all Meta War Room members
─────
INTERVIEW INTEL
@user2: Phone screen was LC 200 + follow-up
Difficulty: ⭐⭐⭐⭐☆
↑ 156
─────
```

**Broadcasting Logic:**
```
Post created → starts in origin feed (School or Company)
↓
If upvotes ≥ 20: Broadcast to School Feed
If upvotes ≥ 50: Broadcast to Company Feed (all related)
If upvotes ≥ 200: Broadcast to National Feed
```

### 2. Post Types & Templates

**1. Offer Drop**
```
┌─────────────────────────────────────────┐
│ 🏆 VERIFIED OFFER                       │
│                                         │
│ [Amazon Logo]                           │
│ Software Development Engineer Intern    │
│ Seattle, WA                             │
│ TC: $XX,XXX (optional)                  │
│                                         │
│ Salman Said                             │
│ @salman_goated • UMN CS '27             │
│ 🟢 Verified Offer                       │
│ Posted 2m ago                           │
│                                         │
│ Reactions:                              │
│ 🔥 2.4k  🧠 891  🐐 445  😭 1.2k         │
│                                         │
│ Community Rating: ⭐⭐⭐⭐⭐ 4.8/5        │
│                                         │
│ [View Player Stats] [Compare Similar]   │
└─────────────────────────────────────────┘

Auto-attached context:
↑ +312 National Rank
+1,240 XP
38-day grind streak maintained
```

**2. Grind Session**
```
┌─────────────────────────────────────────┐
│ 🔥 RANKED SESSION COMPLETE              │
│                                         │
│ @salman_goated                          │
│ 2h 14m focus time | +340 XP             │
│ 5 problems (3M, 2H)                     │
│                                         │
│ Patterns improved:                      │
│ • Sliding Window → 85% (+5%)            │
│ • DP 2D → 62% (+8%)                     │
│                                         │
│ 🔥 38-day streak                        │
└─────────────────────────────────────────┘
```

**3. Career Event**
```
┌─────────────────────────────────────────┐
│ 📧 CAREER UPDATE                        │
│                                         │
│ @salman_goated advanced to Final Round  │
│ Stripe • SWE Intern                     │
│ 🟢 Verified via email scan              │
│                                         │
│ Timeline:                               │
│ Applied → OA → Phone → Final (YOU ARE HERE) │
│                                         │
│ Success rate: 67% → Offer              │
│ Avg decision time: 8 days              │
└─────────────────────────────────────────┘
```

**OFFER DROP**

```
┌─────────────────────────────────────────┐
│ 🏆 NEW OFFER                            │
│                                         │
│ [Amazon Logo]                           │
│ Software Development Engineer Intern    │
│ Seattle, WA                             │
│ TC: $XX,XXX - $XX,XXX (optional) Levels.FYI        │
│                                         │
  Salman Said                             │
│ @salman_goated • UMN CS '27             │
│ 🟢 Verified Offer                       │
│ Posted 2m ago                           │
│                                         │
│ ─────────────────────────────────────   │
│ Reactions:                              │
│ 🔥 2.4k  🧠 891  🐐 445  😭 1.2k         │
│                                         │
│ Community Rating: ⭐⭐⭐⭐⭐ 4.8/5        │
│ (3.2k votes)                            │
│                                         │
│ [View Player Stats] [Compare Similar]   │
└─────────────────────────────────────────┘
```



**4. Job Drop (Company Feed)**
```
┌─────────────────────────────────────────┐
│ 🔴 LIVE DROP                            │
│                                         │
│ UBER OA INVITES SENDING NOW             │
│ Reported by 47 users in last hour       │
│                                         │
│ @user1: Just got OA (10:23am)           │
│ @user2: Me too (10:31am)                │
│ @user3: Same (10:45am)                  │
│ ... +44 more                            │
│                                         │
│ OA Type: 2x LC Medium (reported)        │
│ Deadline: 7 days from receipt           │
└─────────────────────────────────────────┘
```

**5. Purge Announcement**
```
┌─────────────────────────────────────────┐
│ 💀 WEEKLY PURGE COMPLETE                │
│                                         │
│ 847 accounts deleted                    │
│ 1,203 users on probation                │
│ 89% of platform still active            │
│                                         │
│ Top Survivor: @jenny_grindqueen         │
│ Most Improved: @rookie_coder            │
│                                         │
│ Next purge: 6 days 14 hours             │
│ Your status: ✅ SAFE (127% ROI)         │
└─────────────────────────────────────────┘
```

**6. Confession Wall Post (Anonymous)**
```
┌─────────────────────────────────────────┐
│ 😭 CONFESSION                           │
│                                         │
│ Anonymous • UMN CS '27 • Rank #2,847    │
│ Posted 5m ago                           │
│                                         │
│ "600 LC problems, 0 offers. I'm        │
│  starting to think I'm cooked. Anyone   │
│  else struggling this hard?"            │
│                                         │
│ Reactions:                              │
│ 😭 1.2k  💀 445  🫂 892                  │
│                                         │
│ 234 Comments (supportive thread)        │
└─────────────────────────────────────────┘
```

### 3. Anonymous Posting

**How It Works:**
```
User clicks "Post Anonymously"
↓
Select category:
- 😭 Struggling
- 🎉 Small Win
- ❓ Advice Needed
- 💭 Random Thought
- 🔥 Hot Take
- Offers/OAs/Career Stuff
↓
Write post (max 500 chars)
↓
Post shows:
- "Anonymous" (username hidden)
- School + Grad Year (preserved for context)
- Rank range (not exact: "Ranked #2,000-3,000")
- Stats blurred
↓
Post to Confession Wall feed
```

**Privacy Guarantees:**
- Username never revealed
- IP not logged
- Cannot trace back to user (even for mods)
- Only aggregate stats shown

**Confession Wall Rules:**
- No doxxing yourself (mentioning your name)
- No attacks on other users
- Supportive environment
- Toxic confessions = removed

### 4. Comment System (Smart Comments)

**Auto-Attached Stats:**
```
When you comment, your profile stats show:

@competitive_andy
#1,247 National | 234 LC | 0 Offers | Credibility: 623
"Finally bro 😭"

─────

@jenny_grindqueen
#203 National | 523 LC | 2 Offers | Credibility: 891
"Huge W, congrats!"

─────

This creates context:
- High-rank users = more weight
- 0 offers + 234 LC = different perspective
- Credibility score = trust signal
```

**Comment Threading:**
- Nested replies (up to 3 levels deep)
- Sort by: Top (most upvotes), New, Controversial
- Collapse/expand threads

### 5. Reaction System

**Allowed Reactions (Weighted by Credibility):**
```
🔥 Cracked (respect)
🧠 Big Brain (smart play)
🐐 GOAT (generational)
💀 Finally (took long enough)
😭 Robbed / Relatable
📉 Mid (the toxicity outlet)
🫂 Supportive (for confession wall)
🎉 Congrats
```

**Reaction Weighting:**
```
Your credibility score = reaction weight

User with 1000 credibility → 1.0x weight
User with 500 credibility → 0.5x weight
User with 100 credibility → 0.1x weight

Display:
🔥 2,447 raw reactions
(weighted: 1,892 credibility points)

This prevents spam from low-quality accounts
```

### 7. Bounty System (XP-Based Help Marketplace)

**How Bounties Work:**
```
USER A NEEDS HELP:
Posts bounty in feed or DMs:
"Need resume review for FAANG apps
Bounty: 300 XP
Deadline: 48 hours"
↓
XP locked in escrow (User A's balance - 300 XP)
↓
USER B CLAIMS BOUNTY:
"I'll help, send resume"
↓
User B provides help (resume review)
↓
USER A CONFIRMS:
"Thanks, this helped!"
Marks bounty as complete
↓
XP transferred: User A → User B (+300 XP)
↓
If User A doesn't confirm in 7 days:
- Auto-release XP to User B
- User A penalized -50 credibility
```

**Bounty Categories:**
- Resume Review (100-500 XP)
- Mock Interview (300-1000 XP)
- Referral (500-2000 XP, paid on interview)
- Code Review (100-300 XP)
- Career Advice (50-200 XP)

**Bounty Marketplace:**
```
ACTIVE BOUNTIES (23)

🎯 RESUME REVIEW - 300 XP
@user1: "Need FAANG resume feedback"
Deadline: 1d 14h
[Claim Bounty]

🎯 MOCK INTERVIEW - 800 XP
@user2: "Practice Meta-style phone screen"
Deadline: 3d 2h
[Claim Bounty]

🎯 REFERRAL - 1,500 XP
@user3: "Need Google referral, have stats"
Deadline: 7d
[Claim Bounty]
```

**Bounty Leaderboard:**
```
TOP BOUNTY HUNTERS (This Month)

#1 @jenny_helper - 23,400 XP earned
   ├─ Bounties completed: 47
   └─ Success rate: 94%

#2 @career_coach - 18,900 XP earned
   ├─ Bounties completed: 34
   └─ Success rate: 97%
```

### 8. Direct Messaging (DMs)

**DM Features:**
- One-on-one private messaging
- Send text, images, links
- Share LC problems, offers, resumes
- Block/mute users
- Report abusive DMs

**DM Contexts:**
- Mentorship (high-rank → low-rank)
- Accountability partners
- Bounty coordination
- Referral discussions
- General networking

### 11. Trending & Discovery

**Trending Topics:**
```
TRENDING NOW

#meta (2,847 mentions today)
#struggling (1,203 mentions)
#leetcode (891 mentions)
#offers (445 mentions)
```

**Explore Page:**
```
DISCOVER

Top Users This Week:
#1 @jenny_grindqueen (+500 rank jump)
#2 @speedrun_god (100 LC in 7 days)
#3 @helper_hero (10 bounties completed)

Top Posts This Week:
🏆 "First FAANG offer after 600 LC" - 12k reactions
😭 "600 LC, 0 offers" confession - 8k reactions
🔥 "How I went 0 → 200 LC in 30 days" - 6k reactions
````

---

# ENGINE 4: RANK ENGINE - WORK IN PROGRESS

## Core Purpose
**The central truth system. Calculates ranks, manages Elo, handles LP, runs seasons, integrates all data.**

## What This Engine Does

### 1. Multi-Dimensional Ranking

**Five Separate Rankings:**
```
Every user has 5 ranks:

1. DSA Rank (LeetCode performance)
2. Career Rank (Offers, interviews, OAs)
3. Project Rank (GitHub, experience)
4. Interview Rank (Interview performance)
5. Contribution Rank (Platform ROI, posts)

Composite Overall Rank = weighted blend:
DSA: 30%
Career: 35%
Project: 15%
Interview: 10%
Contribution: 10%
```

**Example User Ranks:**
#### Profile Stats (Always Visible)
```
Salman Said
@currentlycrafting
🎓 UMN CS '27
🏆 Rank: #421 National | #10 UMN
📊 Credibility: 847 / 1000

Career
├─ Offers: 2 (Target SWE Intern)
├─ Interviews: 31
├─ OA Pass Rate: 23%
└─ Apps Sent: 403

DSA
├─ LC Solved: 412 (E: 180, M: 187, H: 45)
├─ Pattern Mastery: 14/18
├─ Current Streak: 38 days
└─ Locked-In Time: 127 hours


TABLE

Contributions
├─ Job Drops: 23
├─ Quality Posts: 156
├─ Upvote Ratio: 0.73
└─ Platform XP: 8,441
```

LP Range per Division:
Challenger: 1000+ LP
Grandmaster: 800-999 LP
Master: 600-799 LP
Diamond: 450-599 LP
Platinum: 350-449 LP
Gold: 250-349 LP
Silver: 150-249 LP
Bronze: 0-149 LP

Gaining LP:
- Complete activities (LC sessions, offers, etc.)
- Win duels
- High performance grades (S+, S, A)
- Streaks

Base LP from activity:
- LC Easy (S+ grade): +5 LP
- LC Medium (S+ grade): +12 LP
- LC Hard (S+ grade): +25 LP
- Verified offer (FAANG): +50 LP
- Duel win (equal Elo): +15 LP

Multipliers:
- Streak bonus: +15%
- Performance grade: S+ (2.0x), S (1.5x), A (1.2x), B (1.0x)
- Win streak (duels): +10% per consecutive win

Example:
Hard problem (25 base) * 
S-tier (1.5x) * 
38-day streak (1.15x) = 
43 LP gained
```

**Promotion/Demotion:**
```
User at 598 LP (Diamond)
Completes Hard LC (S-tier) → +43 LP
New LP: 641 LP
↓
PROMOTION TO MASTER!

Notification:
┌─────────────────────────────────────────┐
│ 🎉 DIVISION PROMOTION                   │
│                                         │
│ You've been promoted to MASTER!         │
│                                         │
│ Diamond → Master                        │
│                                         │
│ New perks unlocked:                     │
│ • Master profile border                 │
│ • Exclusive Master badge                │
│ • +20% XP bonus                         │
│                                         │
│                            │
└─────────────────────────────────────────┘
```

### 3. Elo Rating System

**Separate Elo per Category:**
```
User has Elo for:
├─ DSA Elo (based on LC performance)
├─ Duel Elo (based on 1v1 duel record)
├─ Career Elo (based on offer quality)
└─ Contribution Elo (based on post quality)

Elo Range:
2400+: Grandmaster level
2000-2399: Master level
1600-1999: Diamond level
1200-1599: Platinum level
800-1199: Gold level
400-799: Silver level
0-399: Bronze level
```

**Duel Elo Calculation:**
```
User A (Elo 1500) vs User B (Elo 1600)

User A wins:
Expected win prob: 36%
Actual result: Win
Elo gain: +24 (upset victory)

User A's new Elo: 1524
User B's new Elo: 1576 (-24)

If User B had won (expected):
User B gain: +16 (expected win)
User A loss: -16
```

**Matchmaking (Duels):**
```
User queues for ranked duel
Current Duel Elo: 1524
↓
System searches for opponent within ±100 Elo
Found: Opponent (Elo 1589)
Elo difference: 65
↓
Match created
Estimated odds: 45% vs 55%
LP Wager: 15 LP each
↓
Winner gets: +15 LP + Elo gain
Loser gets: -15 LP + Elo loss
```

### 4. Hidden MMR (Matchmaking Rating)

**What is MMR:**
```
MMR = Your "true skill" (hidden from users)

Separate from visible rank/Elo
Used for matchmaking in duels
Adjusts faster than visible rank
Prevents smurfing (new accounts dominating)

MMR vs Rank:
- High MMR, low rank → climbing fast (new skilled player)
- Low MMR, high rank → falling (boosted or declining player)
```

**MMR Calculation:**
```
Factors:
├─ Win/loss record (duels)
├─ Performance grades (LC sessions)
├─ Consistency (streaks)
├─ Speed of improvement
└─ Opponent difficulty (who you beat/lose to)

Example:
User with 1500 visible Elo but 1800 MMR
→ System matches them against 1800 Elo opponents
→ If they keep winning, rank catches up to MMR
→ If they lose, MMR drops to match rank
```

### 5. Performance Grading (S+ to F)

**Grade Impact on LP:**
```
S+ Tier: 2.0x LP
S Tier: 1.5x LP
A Tier: 1.2x LP
B Tier: 1.0x LP
C Tier: 0.8x LP
D Tier: 0.5x LP
F Tier: 0.0x LP (no LP, maybe loss)
```

**Grade Calculation (LC):**
```
Factors:
├─ First attempt success (yes/no)
├─ Time vs average (faster = better)
├─ Optimal complexity (time/space)
├─ Hints used (none/few/many)
└─ Code quality (clean/messy)

Algorithm:
score = 0
if first_attempt: score += 40
if time < 0.5 * avg_time: score += 30
if time < 0.75 * avg_time: score += 20
if optimal_complexity: score += 20
if no_hints: score += 20
if clean_code: score += 10

Grade:
90-100: S+
80-89: S
70-79: A
60-69: B
50-59: C
40-49: D
0-39: F
```

### 6. Seasonal Rankings

**Season Structure:**
```
Year divided into 4 seasons:
├─ Fall (Sep-Nov)
├─ Winter (Dec-Feb)
├─ Spring (Mar-May)
└─ Summer (Jun-Aug)

Each season = 3 months
At season end: Soft reset
```

**Soft Reset:**
```
End of season:
User's current LP: 641 (Master)
↓
Soft reset formula:
new_LP = (current_LP + 400) / 2
new_LP = (641 + 400) / 2 = 520
↓
New season starts at 520 LP (high Diamond)

Why soft reset:
- Keeps competition fresh
- Prevents stagnation at top
- Rewards recent performance
- Allows comebacks
```

**Season Rewards:**
```
End of Fall 2026 Season:

Your Finish: #421 National (Master Division)

Next season starts in: 7 days
Placement matches: 10 games to calibrate
```

### 7. Placement Matches (New Users)

**How It Works:**
```
New user joins
↓
Must complete 10 placement matches/activities:
├─ 5 LC problems (ranked sessions)
├─ 3 career events (applications/OAs)
├─ 2 duels
↓
System calculates initial rank based on:
- Performance in LC problems
- Existing career progress
- Duel results
- School/experience level
↓
Placement: #4,567 National (Gold Division, 287 LP)
"You're placed in the top 35% of all users!"
```

**Placement Uncertainty:**
```
During placement matches:
- LP gains are 2x normal (volatile)
- Losses are half normal (forgiving)
- MMR adjusts rapidly
- Rank hidden until placement complete

After placement:
- Normal LP gains/losses
- Rank visible
- MMR stabilizes
```

### 8. Regional & Segmented Rankings

**Multiple Leaderboards:**
```
User can see their rank in:

🌍 Global Rankings:
├─ National: #421 (USA)
├─ State: #87 (Minnesota)
├─ City: #12 (Minneapolis)

🏫 School Rankings:
├─ University: #3 (UMN)
├─ Major: #2 (CS)
├─ Grad Year: #5 (Class of '27)

🏢 Company Target Rankings:
├─ FAANG hunters: #203
├─ Startup hunters: #891
├─ Finance: #1,234

⏰ Time-Based Rankings:
├─ Daily: #12 (most LP gained today)
├─ Weekly: #45 (most LP this week)
├─ Monthly: #156 (most LP this month)
└─ All-Time: #421 (overall)

```

**Rank Display:**
```
YOUR RANKINGS

National: #421 / 32,356 users (Top 1.3%)
School (UMN): #3 / 847 users (Top 0.4%)
Class of '27: #5 / 2,104 users (Top 0.2%)

Your highest rank: UMN #3 🏆
Your climb: ↑ +312 National this week
```

### 9. Streak Bonuses

**How Streaks Work:**
```
Daily Streak = consecutive days with ranked activity

Streak Levels:
3 days: +5% LP/XP
7 days: +10%
14 days: +15%
30 days: +20%
60 days: +25%
100 days: +30%
365 days: +50% (insane)

Example:
38-day streak = +20% bonus
Hard LC (25 base LP) * 1.2 = 30 LP
```

**Streak Protection:**
```
Miss a day?
Streak breaks unless:
- You're on vacation mode (7 days max/season)
- You used emergency grind escape (protects streak)
- Server downtime (automatic protection)
```

### 10. Win/Loss Streak Bonuses (Duels)

**Duel Streaks:**
```
Win Streak:
1 win: +0%
2 wins: +5% LP
3 wins: +10% LP
4 wins: +15% LP
5+ wins: +20% LP

Loss Streak (cushion):
1 loss: -100% LP loss
2 losses: -90% LP loss (protection kicks in)
3 losses: -80% LP loss
4+ losses: -70% LP loss (max protection)

Example:
Win 5 duels in a row:
Normal duel win: +15 LP
With 5-win streak: +15 * 1.2 = +18 LP

Lose 3 duels in a row:
Normal duel loss: -15 LP
With 3-loss streak: -15 * 0.8 = -12 LP (protected)
```

### 11. Rank Decay (Inactivity)

**Decay Schedule:**
```
No activity for:
├─ 3 days → -2% LP
├─ 7 days → -5% LP
├─ 14 days → -15% LP
├─ 21 days → Probation (Purge Engine takes over)

Example:
User at 641 LP (Master)
Inactive for 7 days:
LP decay: -5% = -32 LP
New LP: 609 LP (still Master, but close to demotion)
```

**Decay Exemptions:**
```
NO decay if:
- On vacation mode (max 7 days/season)
- Emergency grind escape active (24hr)
- Server downtime
- Verified medical leave (requires proof)
```

### 12. Rank History & Analytics

**90-Day Rank Graph:**
```
YOUR RANK HISTORY (Last 90 Days)

      #200 ─┐
           │     ╱───╲
      #400 ─┤   ╱     ╲╱╲
           │  ╱          ╲
      #600 ─┼╱             ╲─ (you are here)
           │
      #800 ─┘
           Sep    Oct    Nov    Dec

Key Events:
📍 Nov 15: +312 rank jump (got offer)
📍 Oct 23: -89 rank drop (missed week)
📍 Sep 12: Joined platform (#892)
```

**Insights:**
```
RANK INSIGHTS

Your Growth:
├─ +471 rank improvement (90 days)
├─ Peak: #203 (Nov 18)
├─ Lowest: #892 (Sep 12)
└─ Current: #421

Velocity:
├─ +5.2 ranks/day (avg)
├─ Trending: ↗ Upward
└─ Projection: #200 by Feb 1

Comparison:
├─ You're climbing faster than 78% of users
├─ Your school (UMN) avg: #1,234
└─ You're beating avg by 813 ranks

---

## How the 5 Engines Connect
```
┌─────────────────────────────────────────────────┐
│              CENTRAL MESSAGE BUS                │
│         (Event-Driven Architecture)             │
└─────────────────────────────────────────────────┘
           ↓         ↓         ↓         ↓
    ┌──────────┐ ┌──────────┐ ┌──────────┐
    │  GRIND   │ │  CAREER  │ │  SOCIAL  │
    │  ENGINE  │ │  ENGINE  │ │  ENGINE  │
    └──────────┘ └──────────┘ └──────────┘
           ↓         ↓         ↓
        ┌──────────────────────────┐
        │      RANK ENGINE         │
        │  (Central Truth System)  │
        └──────────────────────────┘
                     ↓
        ┌──────────────────────────┐
        │     PURGE ENGINE         │
        │  (Accountability Layer)  │
        └──────────────────────────┘
```

---
# ENGINE 5: PURGE ENGINE

## Core Purpose
**The accountability enforcer. Tracks ROI, issues warnings, executes purges, manages probation.**

## What This Engine Does

### 1. ROI (Return on Investment) Tracking

**What is ROI:**
```
ROI = Value you contribute back to the platform

Every week, users must generate minimum ROI to survive.

Minimum Weekly ROI: 100 points

How to earn ROI:
├─ LC session XP: 1 XP = 1 ROI
├─ Duel XP: 1 XP = 1 ROI
├─ Career event logged: 50-1000 ROI (based on type)
├─ Quality post (upvotes > 10): upvotes = ROI
├─ Job drop (verified): 100 ROI
├─ Email classification: 50 ROI
├─ Interview question submitted: 100 ROI
├─ Bounty completed: XP earned = ROI
└─ Offer logged (verified): 1000 ROI
```

**Weekly ROI Calculation:**
```
User's Activity This Week:
├─ LC sessions: 3 ranked (total 340 XP) → 340 ROI
├─ Duel won: 180 XP → 180 ROI
├─ Posted offer: verified → 1000 ROI
├─ Comments: 5 quality (avg 12 upvotes) → 60 ROI
└─ TOTAL: 1,580 ROI

Status: ✅ SAFE (1,580% of minimum)
```

**ROI Tracking Dashboard:**
```
YOUR WEEKLY ROI

Current Week: 127 / 100 ROI ✅
Days Remaining: 3

Breakdown:
├─ Grinding: 85 ROI (67%)
├─ Career Events: 0 ROI (0%)
├─ Social Contributions: 42 ROI (33%)

Progress:
[████████████████████░░] 127%

Weekly Streak: 38 consecutive weeks safe
All-Time Average: 156 ROI/week
```

### 2. Purge Stages & Warnings

**Stage 0: Active (Safe)**
```
✅ ACTIVE

ROI this week: 127 / 100
You're safe. Keep grinding.
Next purge: 6d 14h
```

**Stage 1: Warning (3 Days Before Purge)**
```
⚠️ WARNING - 72 HOURS

You haven't met minimum ROI this week.
Current: 23 / 100 ROI

You need 77 more ROI in next 3 days.

Suggested activities:
├─ Complete 3 ranked LC sessions → ~90 ROI
├─ Log an interview → 50 ROI
├─ Make 1 quality post → 20-50 ROI

[Start Grinding Now]
```

**Stage 2: Critical (48hr)**
```
🚨 CRITICAL - 48 HOURS

You're dangerously close to probation.
Current: 45 / 100 ROI

Need 55 ROI in 2 days.

If you miss ROI:
- PROBATION status
- Rank frozen
- Public "On Probation" badge
- Can't vote/comment

[Emergency Grind Escape Available]
```

**Stage 3: Final Warning (24hr)**
```
💀 FINAL WARNING - 24 HOURS

This is your last chance.
Current: 67 / 100 ROI

Need 33 ROI in 1 day = doable!

Missing ROI = PROBATION starting tomorrow.

[Use Emergency Grind Escape] (ONE-TIME)
```

**Stage 4: Probation (Missed ROI)**
```
⚠️ PROBATION

You missed minimum ROI last week.

Restrictions:
├─ Rank frozen (no gains, no losses)
├─ Can't vote on posts
├─ Can't comment
├─ Public "On Probation" badge
├─ Yellow profile border
├─ Listed on Probation Board

To escape probation:
Generate 100 ROI this week to return to Active.

If you miss ROI again = PURGED.
```

**Stage 5: Purged (Missed ROI on Probation)**
```
💀 ACCOUNT PURGED

You failed to generate ROI for 2 consecutive weeks.

Your account has been deleted:
├─ All XP erased
├─ Rank reset
├─ Username released
├─ Email domain blacklisted for 30 days

Exit Survey:
"Why weren't you grinding?"
- Too busy
- Lost motivation
- Platform not valuable
- Other: ___________

You can create a new account after 30 days.
```

### 3. Emergency Grind Escape Hatch

**How It Works:**
```
User on final warning (24hr) clicks:
[Use Emergency Grind Escape]
↓
Confirmation:
"This is a ONE-TIME save per season.
Cost: 100 XP from your total.
You'll be marked SAFE for this week.

Use it? [Yes] [No]"
↓
If YES:
├─ -100 XP deducted
├─ ROI requirement waived for this week
├─ Status: ✅ SAFE
├─ Emergency Grind Escape: USED (can't use again this season)
└─ Next week: normal ROI required
```

**Restrictions:**
- ONE use per season (resets every 3 months)
- Costs 100 XP
- Must have at least 100 XP to use
- Can't use if already on probation

### 4. Probation Board (Public Shame)

**The Wall of Shame:**
```
PROBATION BOARD (1,203 users)

Users who missed ROI this week:
─────
@struggling_andy
Rank: #4,567 (frozen)
Missed ROI: 23 / 100
Days on probation: 1
─────
@lazy_grinder
Rank: #8,921 (frozen)
Missed ROI: 67 / 100
Days on probation: 3
─────
... 1,201 more

[Sort by: Rank, ROI Deficit, Days on Probation]
```

**Probation Escape:**
```
@struggling_andy → ESCAPED PROBATION

Generated 156 ROI this week.
Back to ACTIVE status.
Rank unfrozen.
Congratulations on surviving!
```

### 5. Rank Decay (Inactivity Punishment)

**Decay Rules:**
```
No activity for:
├─ 3 days → -2% rank
├─ 7 days → -5% rank
├─ 14 days → -15% rank
├─ 21 days → Probation automatically
├─ 28 days (on probation) → Purged
```

**Decay Calculation:**
```
User stops grinding on Day 0 (Rank #421)

Day 3: -2% → Rank #429 (-8 spots)
Day 7: -5% → Rank #442 (-21 spots total)
Day 14: -15% → Rank #484 (-63 spots total)
Day 21: PROBATION triggered
Day 28: PURGED if still no activity
```

**Decay Warnings:**
```
⏰ DECAY WARNING

You haven't been active in 5 days.
In 2 days: -2% rank decay
In 9 days: -5% rank decay

[Start Session to Stop Decay]
```

### 6. Public Accountability Commitments

**How It Works:**
```
User posts:
"I commit to solving 50 LC problems by Dec 31"
↓
System tracks:
- Commitment made (public post)
- Deadline: Dec 31
- Progress: 12 / 50 (24%)
↓
If deadline passes and not completed:
- Public "Broken Commitment" badge (7 days)
- -200 XP penalty
- -50 Credibility
↓
If completed:
- Public "Commitment Kept" badge
- +200 XP bonus
- +50 Credibility
```

**Commitment Tracker:**
```
YOUR COMMITMENTS (2 active)

🎯 50 LC by Dec 31
Progress: 12 / 50 (24%)
Deadline: 23 days
On track: No (need 2.5 problems/day)
[Update Progress]

🎯 Get Meta offer by Feb 1
Progress: In finals
Deadline: 54 days
[Update Status]
```

### 7. Weekly Purge Announcement

**Every Sunday at 11:59pm:**
```
System calculates:
- Who met ROI → SAFE
- Who missed ROI (first time) → PROBATION
- Who missed ROI (on probation) → PURGED

Purge executes:
├─ Delete purged accounts
├─ Move others to probation
├─ Generate purge announcement
```

**Purge Announcement Post:**
```
┌─────────────────────────────────────────┐
│ 💀 WEEKLY PURGE COMPLETE                │
│                                         │
│ 847 accounts DELETED                    │
│ 1,203 users moved to PROBATION          │
│ 89% of platform still ACTIVE            │
│                                         │
│ 🏆 Top Survivors:                       │
│ #1 @jenny_grindqueen (2,847 ROI)       │
│ #2 @speedrun_god (1,992 ROI)           │
│ #3 @helper_hero (1,556 ROI)            │
│                                         │
│ 📊 Most Improved:                       │
│ @comeback_kid (+500 rank this week)    │
│                                         │
│ Next purge: 6 days 23 hours 59 minutes │
│                                         │
│ YOUR STATUS: ✅ SAFE (127% ROI)         │
└─────────────────────────────────────────┘
```

### 8. Purge Countdown Timer

**Always Visible (Top Bar):**
```
⏰ NEXT PURGE: 6d 14h 23m

Your Status: ✅ SAFE (127 / 100 ROI)

[Click for Details]
```

**Detailed View:**
```
PURGE COUNTDOWN

Next purge: Sunday, Dec 8, 11:59pm (6d 14h 23m)

Your Week So Far:
├─ ROI: 127 / 100 ✅
├─ Rank movement: ↑ +14
├─ Streak: 38 weeks safe

Projected Status: ✅ SAFE
(assuming you maintain activity)

Platform Stats:
├─ Active users: 12,847
├─ On probation: 1,203 (9%)
├─ At risk this week: 2,456 (19%)

[View Probation Board]
```

### 9. Purge Analytics & Insights

**Personal Purge History:**
```
YOUR PURGE HISTORY

Weeks Survived: 38 / 38 (100%)
Average ROI: 156 / week
Peak ROI: 2,847 (offer week)
Lowest ROI: 102 (close call!)

Close Calls: 3 times
├─ Week 12: 103 ROI (just safe)
├─ Week 24: 107 ROI (close)
└─ Week 31: 102 ROI (very close!)

Emergency Escapes Used: 0 / 1 this season
```

**Platform Purge Stats:**
```
PURGE STATISTICS

Since Launch:
├─ Total accounts created: 45,203
├─ Total accounts purged: 12,847 (28%)
├─ Currently active: 32,356 (72%)

This Season:
├─ Purged: 3,421 (10% of active)
├─ Avg ROI: 178 / week
├─ Top survivor: @jenny_queen (12,456 avg ROI)

Most Common Purge Reasons:
1. Stopped grinding (67%)
2. Only lurking, not contributing (23%)
3. Lost motivation (10%)
````
