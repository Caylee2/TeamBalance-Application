# TeamBalance

TeamBalance is a web application built to help student and professional teams divide project work fairly and prevent free-riding. Using the Gemini API and a custom workload-balancing algorithm, it breaks down project topics into actionable sub-tasks and assigns them based on each member's skills and availability.

## Overview

Group projects often suffer from uneven workloads, where a few members end up doing most of the work while others contribute very little. TeamBalance addresses this by combining automated task breakdown with an optimization engine that prioritizes equal work hours across the entire team.

## Core Features

- **Automated Task Breakdown:** Enter a project topic or brief description, and the app uses `gemini-3-flash-preview` to generate a structured list of tasks with estimated hours, difficulty ratings (1–5), and categories (Development, Design, Planning, Presentation). An offline fallback mode is also included so the app works without an API key.
- **Skill-Based Team Profiles:** Add team members along with their weekly available hours and skill ratings across four core areas. To prevent inflated self-assessments, each member is limited to a maximum of two 5-point ratings.
- **Balanced Task Allocation:** The distribution algorithm guarantees that every team member receives at least one task. For remaining tasks, it applies a non-linear penalty to accumulated hours alongside skill-matching weights, keeping total work-hour differences across members as small as possible.
- **Fairness Metrics and Comparison:** After running the allocation, the app calculates a team fairness score out of 100 based on the standard deviation of assigned hours and displays a side-by-side bar chart comparing each member's total workload.

## Tech Stack

- **Frontend:** HTML5, Vanilla JavaScript (ES6+)
- **Styling:** Tailwind CSS (CDN), Pretendard Font, FontAwesome
- **Charts:** Chart.js
- **AI Integration:** Google Gemini API (`gemini-3-flash-preview`)

## Getting Started

TeamBalance runs entirely in the browser as a single HTML file, so no build steps or backend servers are required.

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/TeamBalance.git
   cd TeamBalance
   ```

2. Open `index.html` in any modern web browser.

3. *(Optional)* Click **API Key Settings** in the top header to enter your Google Gemini API key (stored locally in your browser via `localStorage`), or click **Load Sample Data** to populate the app with sample team members and tasks immediately.

## Usage Workflow

1. **AI Task Breakdown:** Describe your project goal to generate an initial list of tasks.
2. **Team & Tasks Setup:** Add your team members, set their skill levels, and review or adjust the generated tasks.
3. **Fair Distribution Results:** Run the allocation engine to view the fairness score, compare assigned hours between teammates, and check individual task lists.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.