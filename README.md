# 👥💕 Nynaleath's Basic Relationship System 

A lightweight dynamic relationship system for AI Dungeon designed to make NPC relationships develop more naturally, consistently, and realistically.

# ✨ What is this?

I designed this system to make interactions and relationships between the player and NPCs more dynamic and believable in AI Dungeon.

One of the problems with AI-driven relationships is that the AI can sometimes invent or ignore established information in order to satisfy the player's actions. Even when important character information is already defined in Story Cards or Plot Components, the AI may occasionally bend or completely ignore it.

For example, an NPC who is explicitly established as gay may suddenly become attracted to the player despite the player's gender being incompatible with their orientation, simply because the player flirted with them. Characters may also become close friends or develop romantic feelings after very few interactions, without enough meaningful development to justify it.

Basic Relationship System is designed to help reduce these inconsistencies.

Instead of relying entirely on the AI to remember and interpret every previous interaction, the system maintains persistent relationship values for each tracked NPC and provides the AI with additional context about their current relationship with the player.

The system also takes character information such as:

- Sexual orientation
- Gender
- Existing romantic relationships
- Existing crushes or love interests
- Hobbies
- Likes
- Dislikes

into account when determining how relationships develop.

The goal is not to replace the AI's narrative judgment, but to give it a more consistent foundation to work from.

The system was originally created for 🎸 A Rising Rockstar Life 🎸 and was also implemented in 📁 Framed.

---

# 💡 How it works

Basic Relationship System tracks two independent relationship dimensions:

👥 Friendship
How positively or negatively the NPC feels toward the player as a person.

💕 Romance
The NPC's romantic feelings toward the player.

These values are independent.

For example:

- An NPC can become a close friend without developing romantic feelings.
- An NPC can have romantic interest without being a close friend.
- A player can improve friendship without automatically increasing romance.
- Romantic feelings can develop more slowly when the NPC already has a crush, is in love, is in a relationship, or is married.
- An NPC can dislike something the player likes without automatically becoming hostile toward them.
- Repeatedly defending or praising something the NPC strongly dislikes can gradually damage friendship.

This separation allows relationships to develop in a more natural way instead of following a simple friendship → romance progression.

---

# 🧠 Character consistency

One of the main purposes of the system is to help preserve information that has already been established about NPCs.

The system reads relevant information from NPC Story Cards, including:

Sexual orientation and gender

Romantic compatibility is checked using the NPC's established gender and sexual orientation.

If an NPC is romantically incompatible with the player, the system prevents the relationship from developing romantic attraction toward the player.

The AI is explicitly instructed not to change the NPC's sexuality or invent a sudden exception simply to accommodate the player's romantic actions.

Existing romantic relationships

NPCs who already have:

- A crush
- Someone they are in love with
- A romantic partner
- A spouse

have reduced romantic receptivity toward the player.

This makes romantic development significantly more difficult and consequential.

Hobbies, likes and dislikes

The system also reads the NPC's:

- "Hobbies:"
- "Likes:"
- "Dislikes:"

from their Story Card.

Shared hobbies and likes can provide small friendship bonuses.

Simply mentioning something an NPC dislikes does not automatically cause a negative reaction.

However, repeatedly praising, defending, or insisting on something the NPC dislikes can gradually reduce friendship.

This allows personal preferences to influence relationships without making every disagreement feel disproportionately important.

---

# 🐢 Designed for gradual relationship development

Basic Relationship System is designed so that relationships do not need to change dramatically after every interaction.

Small social interactions produce small changes.

Meaningful conversations and supportive moments produce larger changes.

Strong negative interactions can damage the relationship significantly.

Romance is intentionally more restrictive than friendship and is affected by both the NPC's existing romantic situation and their friendship with the player.

The system does not randomly turn friendship into romance simply because two characters have interacted many times.

Instead, romantic development is primarily driven by romantic interactions recognized by the system and the context established by the story.

The goal is to make relationship progression feel earned rather than automatic.

---

# 📊 Relationship Status Display

The system can automatically generate a Relationship Status Story Card for tracked NPCs.

The display shows the current values for:

👥 Friendship
💕 Romance

along with their corresponding descriptive relationship level.

For example:

«Friendship: 42.5 — Friend
Romance: 12.7 — Mild Attraction»

The numbers displayed on the Relationship Status card are rounded for readability.

However, the system internally keeps and calculates the actual decimal values.

For example, the display may show:

«Friendship: 12.4»

while the internal value may contain additional decimal precision resulting from several smaller bonuses and penalties.

This allows relationship progression to remain gradual and prevents small interaction effects from being lost simply because the display uses rounded numbers.

The Relationship Status card also indicates when a tracked NPC is currently active in the scene.

---

# 👥 Scene tracking

Basic Relationship System includes a lightweight scene tracker.

The system attempts to determine which tracked NPCs are currently involved in the scene using the player's current action and recent story history.

This allows relationship changes to be applied to the NPC who is actually being interacted with instead of indiscriminately modifying every tracked character.

When multiple NPCs are present and the player's action is ambiguous, the system avoids guessing.

For example, if two NPCs are present and the player writes an ambiguous action such as:

«"I smile at them."»

the system does not automatically assign that interaction to one of the NPCs.

This helps prevent unintended relationship changes.

The scene tracker also allows an NPC to remain active for a few turns after being detected, making normal conversations and interactions feel more continuous.

---

# 🔌 Compatibility

Basic Relationship System is designed as a standalone system.

It does not require Inner Self and does not depend on Inner Self to function.

It has not been tested with:

- 🎭 Inner Self
- 🎴 Auto Cards
- Other community-created AI Dungeon scripts

Compatibility with other scripts may therefore vary depending on how those scripts modify Story Cards, Context, Input, Output, or State.


---

# 📦 Installation

Requirements

- AI Dungeon script edit mode
- Basic familiarity with AI Dungeon scripting
- NPC Story Cards containing the information required by the system

Setup

1. Copy the Basic Relationship System Library into your Library.
2. Copy the Basic Relationship System Input into your Input block.
3. Copy the Basic Relationship System Context into your Context block.
4. Copy the Basic Relationship System Output into your Output block.
5. Create or use the Basic REL v2 — Relationship Status Configuration Story Card.
6. Enter the exact names of the NPCs you want to track in the configuration card.
7. Start your scenario.

The system will automatically create and update the Relationship Status cards for the tracked NPCs.

For best compatibility, character names should match the names used in their Story Cards.

---

# ⚙️ Configuration

The configuration card allows you to specify which NPCs should have a visible Relationship Status card.

Example:

Tracked Characters:
Elio, Sarah, Lucien

Only characters listed in the configuration card receive a visible Relationship Status card.

The relationship system can still maintain internal relationship data for other recognized NPCs.

You can edit the configuration card at any time during an adventure.

---

# 📜 Relationship States

## 👥 Friendship

Enemy
→ Persona Non Grata
→ Neutral
→ Acquaintance
→ Friend
→ Good Friend
→ Best Friends

## 💕 Romance

No Romantic Interest
→ Mild Attraction
→ Romantic Interest
→ Falling in Love
→ Sweethearts
→ Soulmates

These labels are primarily used to give the AI a meaningful description of the current relationship state rather than exposing relationship values alone.

---

# 🎯 Recommended use

Basic Relationship System is best suited for:

- 👥 Scenarios with multiple NPCs
- 💕 Romance and relationship-focused scenarios
- 🐢 Slow or gradual relationship development
- 🎭 Character-driven stories
- 🏠 Slice-of-life scenarios
- 📖 Stories where the player can build relationships with NPCs
- 🧠 Scenarios where NPC personality and established character information are important
- ❤️ Scenarios where NPCs should react differently depending on their sexuality, romantic situation, preferences, and previous interactions

It can be particularly useful in scenarios where the player is free to interact with many different NPCs and the author wants those relationships to develop independently.

It may be less useful for scenarios where:

- Relationships are intentionally instantaneous.
- NPC sexuality or romantic status is not relevant.
- Relationships are completely predetermined.
- The player is not expected to build relationships with NPCs.
- Relationship progression is entirely controlled by explicit scripted choices.

---

# 📜 License

This project is licensed under the MIT License.

You are free to:

- Use the system in your own scenarios.
- Modify it.
- Integrate it into your own projects.
- Publish scenarios containing it.
- Redistribute modified versions.

Credit is not required, but greatly appreciated.

If you use or modify this system in your scenario, I'd love to be credited with a mention and, if possible, a link to this repository or my AI dungeon page.

Attribution

Basic Relationship System
Created by Nynaleath

Originally developed for 🎸 A Rising Rockstar Life 🎸 and also implemented in 📁 Framed.

---

# ❤️ Credits

Created by Nynaleath.

Originally developed for 🎸 A Rising Rockstar Life 🎸.

Also implemented in 📁 Framed.

Thank you for giving Basic Relationship System a try!

If you use it in one of your scenarios, I'd love to see what you build with it — and credit is always appreciated.
