# Blue Green Deployment

Two environments:
- Blue (current)
- Green (new)

Service switches traffic between them.

Advantages:
- Zero downtime
- Instant rollback
- Safe deployment

Disadvantages:
- Double resources
- Higher cost

Steps:
1. Deploy blue
2. Deploy green
3. Service -> blue
4. Switch service -> green
5. Rollback if needed
