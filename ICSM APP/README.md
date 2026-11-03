# Gameplan

Gameplan collects an athlete's sport, goal, experience, schedule, equipment, and training limits. The app then asks sport- and goal-specific follow-up questions and uses those answers to create a sourced weekly workout plan.

## Run locally

The app needs its local API server; opening `index.html` directly will not provide workout generation.

1. Install Node.js 20 or later.
2. Set `OPENAI_API_KEY` in your shell to an API key with Responses API access. The key stays on the server and is never sent to the browser.
3. Optionally set `OPENAI_MODEL` to a model available to your API account. The default is `gpt-5.5`.
4. Start the app from this folder:

   ```powershell
   $env:OPENAI_API_KEY = "your-api-key"
   npm start
   ```

5. Open <http://localhost:3000>.

The API uses web search to research each entered sport and goal, requests structured JSON for follow-up questions and training sessions, and displays source links with generated workouts. Recommendations are informational and should be reviewed by a qualified coach, especially for youth athletes or anyone with an injury or medical restriction.

## API endpoints

- `POST /api/follow-up` accepts the initial survey profile and returns tailored questions.
- `POST /api/workouts` accepts the profile plus follow-up answers and returns weekly sessions and references.
