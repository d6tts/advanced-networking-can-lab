# GitHub Copilot Design Log

## Interaction 1 – Network Design

Prompt:

Copilot Recommendation:

My Evaluation:

Technical Reason:

# GitHub Copilot Design Log

## Interaction 1 – Campus Endpoint Inventory

### Prompt

I am designing a college campus network with three two-story buildings.

Building A:
20 lab computers, 10 lab computers, 10 classroom computers, 18 office workstations, and 18 printers.

Building B:
15 lab computers, 9 classroom computers, 14 office workstations, and 14 printers.

Building C:
8 classroom computers, 11 office workstations, and 11 printers.

Calculate the total wired endpoints for each building and the entire campus. Recommend an appropriate number of access switches and explain your reasoning. Include room for future expansion.
### Copilot Recommendation

| Building | Wired endpoints |
|---|---:|
| A | 76 |
| B | 52 |
| C | 30 |
| **Campus total** | **158** |

A practical starting point is **six access switches**, with at least one in each floor’s wiring closet: **two 48-port switches in A, two 48-port switches in B, and two 24-port switches in C**. That provides 96 ports in A, 96 in B, and 48 in C—**82 spare ports total** for growth (20, 44, and 18 spare, respectively).

This assumes endpoint placement on each floor fits within that floor’s switch capacity. Confirm the floor-by-floor counts and cable distances before ordering; uneven distributions may require different port sizes or additional switches.
### My Evaluation

I took advice from Copilot and decid to go with the info it helped give me.

### Technical Reason

I compared Copilot's calculations with the requirements of the assignment to make sure the endpoint totals were correct and that the recommended switches could support the connected devices and future expansion.
