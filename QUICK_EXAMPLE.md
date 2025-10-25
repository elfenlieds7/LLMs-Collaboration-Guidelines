# Quick Example - Using the Framework

> **Scenario**: Setting up this framework for a new React + Node.js e-commerce project
> **Time**: 15 minutes

---

## Before: Traditional Approach

```
Developer: "Help me build an authentication module"

AI: "Sure! I'll create the files..."
[AI creates 10 files, makes architectural decisions, commits directly]

Developer: "Wait, I wanted JWT not sessions!"
Developer: "And why did you commit without asking?"
```

**Problems**:
- AI makes unauthorized decisions
- No structured workflow
- Lost time fixing unwanted changes

---

## After: Using This Framework

### Step 1: Setup (5 min)

```bash
# Copy templates
cp -r llm-collaboration-template/* my-ecommerce-app/

# Replace placeholders
find my-ecommerce-app -type f -name "*.md" \
  -exec sed -i 's/\[PROJECT_NAME\]/ShopApp/g' {} \; \
  -exec sed -i 's/\[AI_TOOL_1\]/Claude Code/g' {} \; \
  -exec sed -i 's/\[AI_TOOL_2\]/ChatGPT/g' {} \;

# Customize quick-ref.md
# Add: npm test, npm run dev, npm run build
```

### Step 2: AI Onboarding (2 min)

```
Human: "Read START_HERE_AI.md"

AI: [Reads file, 2 minutes]
    "Ready. I've reviewed the docs. I'm your senior developer assistant.
     I'll wait for you to assign tasks and approve my proposals.
     What should I work on?"
```

**Result**: AI understands its role immediately

### Step 3: Working on Feature (8 min)

#### 3.1 Task Assignment

```
Human: "Let's work on #12 - Add JWT authentication"

AI: [Reads issue]
    "Got it. This is an authentication module with JWT.
     I see 3 approaches:

     A. Use Passport.js
        Pros: Mature, many strategies available
        Cons: Heavier, more boilerplate

     B. Use jsonwebtoken directly
        Pros: Lightweight, full control
        Cons: More manual work

     C. Use Auth0 SDK
        Pros: Managed service, less security risk
        Cons: External dependency, cost

     Which approach do you prefer?"
```

#### 3.2 Decision

```
Human: "Go with B - jsonwebtoken. Keep it simple for MVP."

AI: "Understood. I'll implement JWT auth with jsonwebtoken.
     I'll create:
     - src/middleware/auth.js
     - src/routes/auth.js
     - Tests in tests/auth.test.js

     Ready to start?"