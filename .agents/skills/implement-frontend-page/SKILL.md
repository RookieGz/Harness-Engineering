---
name: implement-frontend-page
description: Implement one frontend page task from product, design, and API inputs in a staged way. Build static UI first, then state handling, then API integration, then verification.
---

# Purpose
Implement a single frontend page task with clear validation gates.

# Required order
1. read the task file
2. inspect route and component boundaries
3. build static UI with mock data
4. run visual validation
5. add interaction and state handling
6. run state validation
7. integrate API through a service or hook layer
8. run mocked API scenarios
9. run real API smoke or contract checks
10. collect evidence

# Hard rules
- do not skip loading, empty, or error states
- do not start live API integration before static UI is ready
- do not mix broad refactors into a page task
- do not claim completion without screenshots and receipts

# Done when
- required viewports pass
- required states pass
- mocked API scenarios pass
- real API smoke or contract check passes
- screenshots and test output exist
