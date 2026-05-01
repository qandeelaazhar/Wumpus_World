# Wumpus_World
Wumpus World Dynamic Pathfinding Agent 
ABSTRACT: 
This project presents a web-based Wumpus World AI agent that navigates a dynamic grid environment using propositional logic and a knowledge-based system. The agent perceives environmental cues such as breeze and stench to infer safe and unsafe cells. A CNF-based knowledge base and resolution refutation algorithm are implemented to enable logical decision-making. The system demonstrates core AI concepts including reasoning, inference, and intelligent agent behavior. 
Problem Statement: 
The objective of this project is to develop a web-based dynamic pathfinding agent that can intelligently navigate a Wumpus World-style grid. The agent must: 
Operate in a randomly generated grid environment  

Avoid hidden hazards (pits and Wumpus)  

Use percepts to infer safe paths  

Maintain a knowledge base using propositional logic  

Apply resolution refutation to determine safety of cells  

Reach the goal (gold) without dying  

 

System Overview 

The system simulates a Wumpus World environment in which an intelligent agent explores a grid starting from position (0,0). The grid size is dynamic and selected by the user. 

Environment Features: 

Random placement of:  

Pits 🕳️  

Wumpus 👾  

Gold 💖  

Agent starts at top-left corner  

Agent has no prior knowledge of hazards  

Percepts: 

Breeze 💨 → Indicates nearby pit  

Stench 🦨 → Indicates nearby Wumpus  

The agent uses these percepts to update its knowledge base and make logical decisions. 

Technologies Used 

HTML5 → Structure of the web interface  

CSS3 → Styling and UI design  

JavaScript → DOM manipulation  

Python → AI logic and reasoning  

PyScript → Running Python in browser  

 Environment Design 

The environment is a grid-based world where each cell may contain: 

Pit (dangerous trap)  

Wumpus (deadly creature)  

Gold (goal state)  

Grid Properties: 

User-defined rows and columns  

Random hazard generation  

Agent visibility limited to percepts only  

 

Knowledge Base (KB) 

The Knowledge Base stores logical statements about the environment in propositional form. 

Example KB Statements: 

¬P(0,0) → No pit at start  

¬W(0,0) → No Wumpus at start  

P(x,y) → Pit exists at cell  

W(x,y) → Wumpus exists at cell  

Neighbor Rule Example: 

If a breeze is detected at (1,1): 

P(1,2) ∨ P(2,1) ∨ P(0,1) 

This means at least one neighboring cell contains a pit. 

 

CNF (Conjunctive Normal Form) 

All knowledge is stored in CNF format for logical reasoning. 

Example Conversion: 

Breeze rule: 

B(1,1) ⇔ P(1,2) ∨ P(2,1) 

Converted to CNF: 

(¬B ∨ P1 ∨ P2) ∧ (B ∨ ¬P1) ∧ (B ∨ ¬P2) 

CNF allows systematic resolution-based inference. 

Inference Engine (Resolution Refutation) 

The agent uses a resolution-based algorithm to check safety. 

Steps: 

Convert knowledge base into CNF clauses  

Negate the query (e.g., assume cell is unsafe)  

Apply resolution rule:  

Remove complementary literals  

Combine clauses  

If empty clause is produced → contradiction found  

Contradiction means assumption is false → cell is safe  

Example: 

To test safety of (2,2): 

Assume: 

P(2,2) 

If contradiction occurs → cell is safe 
If no contradiction → cell is unsafe 

Agent Working Mechanism 

The agent follows this process: 

Step 1: Perception 

Reads: 

Breeze  

Stench  

Step 2: Knowledge Update (TELL) 

Updates KB with new rules. 

Step 3: Reasoning (ASK) 

Checks whether neighboring cells are safe using resolution. 

Step 4: Action 

Moves to a safe or least risky cell. 

Step 5: Repeat 

Until: 

Gold is found 💖  

Or agent dies 💥  

 

Visualization System: 

The system provides a full web-based UI: 

Grid Visualization: 

Pink theme interface  

Each cell represents a state  

Cell Types: 

🤖 Agent  

💖 Gold  

👾 Wumpus  

🕳️ Pit  

Dashboard Displays: 

Current percepts  

Score  

Inference steps  

Knowledge Base (CNF clauses)  

Algorithm Summary: 

Initialize grid 
Place hazards randomly 
Start agent at (0,0) 
 
WHILE game not finished: 
   Sense environment 
   Update KB (TELL) 
   For each neighbor: 
       Ask KB if safe using resolution 
   Move to safe cell 
   Update score 
END WHILE 

 

Results 

Agent successfully navigates grid using logic  

Avoids unsafe cells using inference  

Dynamically updates knowledge base  

Demonstrates intelligent decision-making  

Challenges Faced 

Designing resolution algorithm  

Handling CNF clauses correctly  

Preventing unsafe moves  

Managing dynamic grid updates  

Integrating Python in browser using PyScript  

Conclusion 

This project demonstrates how an intelligent agent can use logical reasoning instead of random movement. By implementing a knowledge-based system with CNF representation and resolution refutation, the agent is able to make informed decisions in an uncertain environment. The project effectively combines Artificial Intelligence concepts with web development, resulting in an interactive and educational simulation. 

Project Links 

GitHub Repository: https://github.com/qandeelaazhar/Wumpus_World.git 

 

 
