# Prompt Engineering Best Practices

A comprehensive guide to writing effective prompts for AI assistants.

## Table of Contents

1. [Core Principles](#core-principles)
2. [Prompt Structure](#prompt-structure)
3. [Writing Effective Instructions](#writing-effective-instructions)
4. [Context and Constraints](#context-and-constraints)
5. [Output Formatting](#output-formatting)
6. [Common Patterns](#common-patterns)
7. [Troubleshooting](#troubleshooting)
8. [Advanced Techniques](#advanced-techniques)

## Core Principles

### 1. Be Specific and Clear

**Bad:**
```
Write about marketing.
```

**Good:**
```
Write a 500-word blog post about email marketing best practices for B2B SaaS companies.
Focus on subject line optimization, segmentation strategies, and A/B testing.
Target audience: marketing managers with 2-5 years of experience.
Tone: Professional but approachable.
```

**Why it works:** Specific details guide the AI toward exactly what you need.

### 2. Provide Context

**Bad:**
```
Fix this code: [code snippet]
```

**Good:**
```
I'm working on a React application. This component should display a list of users
fetched from an API, but it's showing an error "Cannot read property 'map' of undefined."

Code: [code snippet]
Expected behavior: Display user list
Error: [error message]
Environment: React 18, TypeScript 4.9

Please identify the issue and provide a fix with explanation.
```

**Why it works:** Context helps the AI understand the problem and provide relevant solutions.

### 3. Specify the Format

**Bad:**
```
Tell me about Python data structures.
```

**Good:**
```
Explain Python data structures in a comparison table with the following columns:
- Data Structure Name
- Use Cases
- Time Complexity (access, insert, delete)
- Memory Usage
- Example Code

Cover: lists, tuples, sets, dictionaries, and arrays.
```

**Why it works:** Specifying format ensures you get structured, usable output.

## Prompt Structure

### The CRAFT Framework

**C**ontext - Background information
**R**ole - Who the AI should act as
**A**ction - What you want done
**F**ormat - How to structure the output
**T**one - Writing style and voice

### Example Using CRAFT

```
Context: I'm launching a new productivity app for remote teams.

Role: Act as a senior product marketer with experience in SaaS go-to-market strategies.

Action: Create a product positioning statement and key messaging framework.

Format:
- One-sentence positioning statement
- Three key value propositions (with supporting points)
- Competitive differentiation (table format)
- Target audience definition

Tone: Professional, confident, data-driven
```

## Writing Effective Instructions

### Do's

✅ **Use action verbs**
- "Analyze this code for security vulnerabilities"
- "Generate 10 creative names for..."
- "Refactor this function to improve readability"

✅ **Break down complex tasks**
```
Step 1: Analyze the current code structure
Step 2: Identify areas that violate SOLID principles
Step 3: Propose refactoring approach
Step 4: Show refactored code with explanations
```

✅ **Set boundaries and constraints**
```
Requirements:
- Maximum 200 words
- Use simple language (8th grade reading level)
- No technical jargon
- Include 2-3 concrete examples
```

✅ **Request explanations**
```
Provide the solution and explain:
- Why this approach is optimal
- What alternatives were considered
- Potential trade-offs
```

### Don'ts

❌ **Be vague**
- "Make it better" → Specify what "better" means

❌ **Assume context**
- "Fix the bug" → Describe the bug, provide error messages, share code

❌ **Use ambiguous language**
- "Write something about AI" → Define topic, audience, format, length

❌ **Forget to specify format**
- Result might be essay when you wanted bullet points

## Context and Constraints

### What to Include

1. **Background Information**
   - What you're working on
   - Why you need this
   - What you've tried already

2. **Requirements**
   - Must-have features
   - Nice-to-have features
   - Dealbreakers

3. **Constraints**
   - Technical limitations
   - Time constraints
   - Resource limitations
   - Compatibility requirements

4. **Target Audience**
   - Who will use/read this
   - Their knowledge level
   - Their needs and pain points

### Example with Complete Context

```
I'm building a REST API for a project management tool.

Current Stack:
- Node.js 18
- Express.js
- PostgreSQL
- JWT authentication already implemented

Requirement:
Create an endpoint for creating new tasks with the following fields:
- title (required, string, max 200 chars)
- description (optional, text)
- assignee_id (required, foreign key to users)
- due_date (optional, ISO date)
- priority (required, enum: low/medium/high)

Constraints:
- Must validate all inputs
- Return appropriate HTTP status codes
- Include error handling
- Follow REST conventions
- Add comments for clarity

Please provide:
1. The complete endpoint code
2. Input validation logic
3. Error handling approach
4. Example API request/response
```

## Output Formatting

### Requesting Structured Output

**Tables:**
```
Create a comparison table with these columns: [list columns]
Compare: [list items to compare]
```

**Lists:**
```
Provide output as:
- Numbered list for steps
- Bulleted list for features
- Nested lists for hierarchical info
```

**Code Blocks:**
```
Provide code with:
- Syntax highlighting (specify language)
- Inline comments
- Before/after examples
```

**Sections:**
```
Organize output in these sections:
1. Executive Summary
2. Detailed Analysis
3. Recommendations
4. Next Steps
```

### Format Examples

**Good Format Request:**
```
Analyze this dataset and provide output in this format:

## Overview
[Brief summary]

## Key Findings
1. [Finding]
   - Supporting data
   - Implication

2. [Finding]
   - Supporting data
   - Implication

## Visualizations Recommended
- [Chart type]: [What to show]

## Action Items
- [ ] [Action item with owner]
```

## Common Patterns

### Pattern 1: Role-Based Prompting

```
Act as a [ROLE] with expertise in [DOMAIN].

[TASK DESCRIPTION]

Provide your answer from the perspective of [ROLE], considering [SPECIFIC FACTORS].
```

### Pattern 2: Few-Shot Learning (Examples)

```
Generate product descriptions following these examples:

Example 1:
Input: Wireless mouse, 2.4GHz, ergonomic, 6 buttons
Output: Experience effortless control with our ergonomic wireless mouse. Six programmable buttons and reliable 2.4GHz connectivity make this mouse perfect for productivity and gaming alike.

Example 2:
Input: Laptop stand, aluminum, adjustable height, cooling design
Output: Elevate your workspace with this sleek aluminum laptop stand. Adjustable height and built-in cooling design keep you comfortable and your device running cool all day long.

Now generate a description for:
Input: [YOUR PRODUCT DETAILS]
```

### Pattern 3: Chain of Thought

```
Solve this problem step by step:

1. First, identify [X]
2. Then, analyze [Y]
3. Next, consider [Z]
4. Finally, synthesize findings

Show your reasoning at each step.
```

### Pattern 4: Iterative Refinement

```
First Draft: Generate [CONTENT]

Then refine by:
1. Making it more [SPECIFIC QUALITY]
2. Adding [SPECIFIC ELEMENT]
3. Removing [WHAT TO REMOVE]
4. Ensuring [REQUIREMENT]

Show both initial and refined versions.
```

## Troubleshooting

### Problem: Output is too generic

**Solution:** Add specific constraints and examples
```
Instead of: "Write a marketing email"
Try: "Write a marketing email for [SPECIFIC PRODUCT] targeting [SPECIFIC AUDIENCE]
      with focus on [SPECIFIC BENEFIT]. Include a subject line, personalized greeting,
      2-paragraph body, and clear CTA. Tone: [SPECIFIC TONE].
      Similar to: [EXAMPLE IF AVAILABLE]"
```

### Problem: Wrong format or structure

**Solution:** Be explicit about format
```
Provide output in this exact format:

```json
{
  "summary": "...",
  "details": [...],
  "recommendations": [...]
}
```
```

### Problem: AI misunderstands intent

**Solution:** Clarify with examples or counterexamples
```
I want: [DESCRIBE WITH EXAMPLE]
I don't want: [DESCRIBE WHAT TO AVOID]

For example:
Good: [EXAMPLE]
Bad: [COUNTEREXAMPLE]
```

### Problem: Response is too long/short

**Solution:** Specify length explicitly
```
Provide a response of approximately [X] words.
Include [NUMBER] main points.
Limit each section to [X] sentences.
```

### Problem: Missing important details

**Solution:** Use a checklist
```
Please ensure your response includes:
- [ ] [REQUIREMENT 1]
- [ ] [REQUIREMENT 2]
- [ ] [REQUIREMENT 3]
- [ ] [REQUIREMENT 4]
```

## Advanced Techniques

### 1. Perspective Shifting

Ask the AI to consider multiple viewpoints:
```
Analyze this product decision from three perspectives:
1. Engineering (technical feasibility, maintenance)
2. Business (costs, revenue impact)
3. User (usability, value)

For each perspective, provide pros, cons, and recommendations.
```

### 2. Constraint-Based Creativity

Use constraints to drive creative solutions:
```
Design a user onboarding flow with these constraints:
- Maximum 3 steps
- No video tutorials
- Must work on mobile
- Completion in under 2 minutes
- Suitable for non-technical users

Be creative within these constraints.
```

### 3. Meta-Prompting

Ask the AI to improve your prompt:
```
I want to [GOAL]. Here's my current prompt:

"[YOUR PROMPT]"

Please suggest improvements to make this prompt more effective. Consider:
- Clarity and specificity
- Context provided
- Format specification
- Missing elements
```

### 4. Prompt Chaining

Break complex tasks into a sequence:
```
Prompt 1: "Analyze this codebase structure and list all components"
[Get output]

Prompt 2: "For each component identified above, list dependencies"
[Get output]

Prompt 3: "Based on the components and dependencies, suggest refactoring opportunities"
[Get output]

Prompt 4: "Implement the top refactoring suggestion with full code"
```

### 5. Self-Critique

Ask the AI to evaluate its own output:
```
[YOUR REQUEST]

After providing your response, critique it by:
1. Identifying potential weaknesses
2. Suggesting improvements
3. Noting any assumptions made
4. Providing an alternative approach
```

## Quick Reference Checklist

Before submitting your prompt, check:

- [ ] **Specific goal** - Is it clear what you want?
- [ ] **Context** - Have you provided relevant background?
- [ ] **Constraints** - Are limitations/requirements specified?
- [ ] **Format** - Is output structure defined?
- [ ] **Audience** - Is target user/reader identified?
- [ ] **Tone** - Is style/voice specified?
- [ ] **Examples** - Would examples help clarify?
- [ ] **Completeness** - Does the AI have everything needed?

## Examples: Before and After

### Example 1: Code Review

**Before:**
```
Review this code.
```

**After:**
```
Review this Python function for:
1. Correctness (does it handle edge cases?)
2. Performance (O(n) complexity or better)
3. Readability (clear variable names, comments where needed)
4. Best practices (PEP 8 compliance)

Code:
[PASTE CODE]

Context: This function processes user input from a web form.
Expected input: String up to 1000 characters.

Provide specific suggestions with code examples.
```

### Example 2: Content Creation

**Before:**
```
Write about AI.
```

**After:**
```
Write a 300-word blog post introducing AI to small business owners.

Focus on:
- What AI is (simple definition)
- 3 practical applications for small businesses
- How to get started (first steps)

Tone: Friendly, encouraging, jargon-free
Include: One concrete example from retail or service industry
Format: Short paragraphs (2-3 sentences each)
```

### Example 3: Data Analysis

**Before:**
```
Analyze this data.
```

**After:**
```
Analyze this sales data for Q1 2024:
[PASTE DATA]

Questions to answer:
1. What are the top 3 performing products?
2. Are there any concerning trends?
3. Which customer segments show highest growth?

Provide:
- Summary statistics table
- Key insights (bullet points)
- 3 actionable recommendations
- Suggested visualizations

Focus on insights that could inform Q2 strategy.
```

## Further Learning

- Practice with simple prompts first
- Experiment with different phrasings
- Save prompts that work well
- Build a personal prompt library
- Iterate based on results

Remember: Prompt engineering is a skill that improves with practice. Start with the basics and gradually incorporate advanced techniques.

---

**Need help?** Return to the [main README](README.md) for more examples and resources.
