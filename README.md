# Athlete Management System

![Blog Image](./Images/Landing_Page.png)
This project is for my final year MSc Computer Science dissertation and research work at Teesside University - Middlesbrough FC Project.

### Problem

Athlete performance data is increasingly collected through wearable and performance-tracking technologies. Although many vendors expose structured data via RESTful APIs, differences in schemas, naming conventions, and data models hinder seamless integration and cross-platform analysis. This study addresses these challenges by exploring three heterogeneous data integration strategies, Extract-Transform-Load (ETL), Schema-On-Read, and Data Federation for unifying structured athlete performance data from APIs.  In addition, a secure web-based Athlete Management System (AMS) with an AI-driven analytical component is designed and implemented to demonstrate practical applicability. 

### Project Management

Trello was used as the project management tool to help track the weekly tasks to be completed and the overall progress of the project in an agile framework with a weekly sprint, here is a link [https://trello.com/b/wBSwEDr5/msc-project](https://trello.com/b/wBSwEDr5/msc-project).

GitHub was used for version control and keeping source code on a remote repository, [https://github.com/Carlvinchi/ams](https://github.com/Carlvinchi/ams)

### Design & Implementation

The proposed Athlete Management System (AMS) comprises a Next.js frontend, a FastAPI backend, a PostgreSQL database, and an AI agent implemented using the PydanticAI framework and powered by the Google Gemini 2.5 Pro model. The system enforces secure authentication and role-based access control, enabling differentiated access for athletes, coaches, and administrators. Interactive dashboards support individual and team-level performance visualization, while a conversational interface allows users to query, analyse, and forecast performance data using natural language. The AI agent produces structured, explainable analyses by summarizing historical trends, generating forecasts, and explicitly communicating methodological choices, confidence levels, and limitations. 
Overall, the system demonstrates the feasibility and effectiveness of combining robust data integration strategies with explainable AI to support secure, data-driven decision-making in modern sports performance management.

**System Architecture**
The system architecture of the web app is shown in the Figure 1 below, the system is made of a Next.js frontend and FastAPI backend, PostgreSQL database and an AI agent.

![Figure 1 - System Architecture](./Images/System_Architectur_Diagram.png) Figure 1 - System Architecture

The Figure 2 below shows the use case diagram of the app; the admin user can manage users (adding, updating or deleting users), upload athlete performance data and view the system logs. The coach and athlete user can view and update their profiles, view performance data and chat with AI agent.

![Figure 2 - UML Use Case Diagram](./Images/AMS_Use_Case.png) Figure 2 - UML Use Case Diagram

To illustrate the dynamic interaction between the frontend client and the backend server, a UML sequence diagram is provided in Figure 3. All user requests undergo authentication and authorization before fulfilment.

![Figure 3 - UML Use Sequence Diagram](./Images/System_UML_Sequence_Diagram.png) Figure 3 - UML Use Sequence Diagram

**Backend Implementation**
The backend of the app is made of three (3) main components: FastAPI server, Database server and AI agent

- ***FastAPI Server***: FastAPI is a modern Python web framework that emphasizes high performance and simplicity. It uses type hints to automatically generate API documentation. It is exceptionally fast and fully supports asynchronous programming, making it ideal for building microservices and demanding applications like real-time data processing systems. 
The FastAPI server, serves as the entry point of the backend components and exposes the functionalities of the database and AI agent to external clients through a REST application programming interface (API), most requests to the server are validated using Pydantic validation classes to ensure the correct parameters and datatypes are used for requests. The FastAPI backend contains sub modules for authentication, user management, performance data management, AI agent interactions and logging events.

- ***Database Server***: Figure 4 illustrates the canonical data model for athlete performance data. Performance records sourced from VALD (force_deck_test) and Catapult (catapult_activities) are represented as sessions, while participating entities are modelled as athletes or teams, and measurable outputs are captured as metrics. This unified modelling approach abstracts heterogeneous data sources into a consistent schema, enabling standardized analytics and comparative queries across datasets. 
All persisted data is stored in a PostgreSQL database deployed within a Docker container to ensure portability and environment consistency. PostgreSQL was chosen for its strong support for concurrent transactions, robust ACID compliance, and high-performance execution under multi-user workloads. Additionally, PostgreSQL provides a rich set of indexing mechanisms that optimize diverse data types and query patterns, making it well suited for production-grade and highly concurrent analytical systems.

![Figure 4 - Canonical Data Model](./Images/final_ams_cdm.png) Figure 4 - Canonical Data Model

- ***AI Agent***: Figure 5 shows the architecture of the AI agent, implemented using the PydanticAI framework and powered by Google Gemini 2.5 Pro. The agent is designed to support structured reasoning, reliable tool invocation, and contextual response generation based on performance data and fine-tuned system prompts. PydanticAI is a Python-based agent framework created to help developers build reliable, production-grade applications powered by LLMs. It provides type-safe, structured outputs, works with multiple AI model providers, offers a clean Pythonic API, and includes features like dependency injection, streaming, and built-in observability, with the aim of making AI agent development more predictable and maintainable.

![Figure 5 - AI Agent Architecture](./Images/Agent_Architecture_Diagram.png) Figure 5 - AI Agent Architecture


**Frontend Implementation**

The frontend of the web application serves as the primary user interface (UI) and was developed using Next.js 15 and Tailwind CSS, with JavaScript as the implementation language. Next.js is a React-based framework that supports server-side rendering (SSR), static generation, automatic code splitting, and optimized performance, enabling fast page loads and improved responsiveness compared to purely client-side Single Page Applications (SPAs). Tailwind CSS is a utility-first styling framework that facilitates rapid, consistent, and responsive design without manually writing extensive CSS classes.
Key frontend features include:

1.	Interactive Visualization Dashboards: Tailored views for athlete and coach users that present performance data, trends, and insights in interactive charts and graphs. 
2.	Profile Management: Users can update personal information and upload profile photos with real-time validation and responsive feedback. 
3.	Data Manipulation Controls: Supports searching, filtering, sorting, and paginating large datasets efficiently within the UI. 
4.	CSV File Upload Handling: Client-side CSV parsing for athlete performance data uploads. 
5.	Chat Interface: A conversational interface for interacting with the AI agent, rendering Markdown content, and visualizing forecasted performance data inline.


### Results


The FastAPI documentaion for the backend API, showing the various endpoints and the required parameters.

![Figure 6 - API Documentation](./Images/Backend_API_documentation.png) Figure 6 - API Documentation


The landing page of the web application, showing the features of the app

![Figure 7 - Landing Page](./Images/Landing_Page.png) Figure 7 - Landing Page


The login interface

![Figure 8 - Login UI](./Images/Login_UI.png) Figure 8 - Login UI


The admin dashboard with various buttons for managing users

![Figure 9 - Admin Dashboard](./Images/admin_dashboard_view.png) Figure 9 - Admin Dashboard


The athlete dashboard, showing KPIs and performance visualizations

![Figure 10 - Athlete Dashboard](./Images/Athlete_dashboard.png) Figure 10 - Athlete Dashboard


The coach dashboard with athlete level visualizations

![Figure 11 - Total Distance Visual](./Images/Coach_dashboard_athlete_performance.png) Figure 11 - Total Distance Visual

![Figure 12 - Jump Performance Visual](./Images/Individual_Athlete_Jump_Performance.png) Figure 12 - Jump Performance Visual

![Figure 13 - Left & Right Symmetry Visual](./Images/Individual_athlete_left_right_symmetry.png) Figure 13 - Left & Right Symmetry  Visual

![Figure 14 - Athlete Injury Risk Visual](./Images/Individual_athlete_injury_risk.png) Figure 14 - Athlete Injury Risk Visual

The coach dashboard with team level visualizations

![Figure 15 - Team Total Distance Trend](./Images/Coach_dashboard_team_performance.png) Figure 15 - Team Total Distance Trend

![Figure 16 - Team Force Production Ranking](./Images/Team_force_production_ranking.png) Figure 16 - Team Force Production Ranking

![Figure 17 - Team Left Right Balance Analysis](./Images/Team_left_right_balance_analysis.png) Figure 17 - Team Left Right Balance Analysis

The chat interface with sample conversation

![Figure 18 - Chat Interface](./Images/chat_interface.png) Figure 18 - Chat Interface

Performance analysis by the agent, after user provided details required to retrieve data

![Figure 19 - Performance Analysis](./Images/performance_data_analysis.png) Figure 19 - Performance Analysis


Performance forecast by the agent using historic data as context

![Figure 20 - Performance Forecast](./Images/performance_forecast.png) Figure 20 - Performance Forecast


Detailed forecast analysis by the agent, stating limitations and factors affecting forecast.

![Figure 21 - Forecast Analysis](./Images/performance_forecast_analysis.png) Figure 21 - Forecast Analysis


### Summary
This work contributes a full-stack AMS that integrates secure backend services, role-based access control, interactive performance visualization, and an explainable AI-driven analytical agent. The system effectively enforces authentication and authorization policies while delivering role-specific dashboards tailored to athletes and coaches. The AI agent extends traditional analytics by enabling natural language interaction with performance data, performing contextual analysis, generating structured summaries, and providing actionable recommendations.

A key contribution of the system is its emphasis on explainability in AI-assisted performance forecasting. By explicitly communicating forecasting methods, confidence levels, and sources of uncertainty, the agent aligns with Explainable AI (XAI) principles and supports informed human oversight in high-stakes training and load management decisions. Overall, the results demonstrate the feasibility and value of combining heterogeneous data integration techniques with explainable generative AI in modern athlete management systems.

### Limitations
The quality of the AI agent’s analysis is inherently dependent on the completeness, accuracy, and consistency of the underlying performance data. As observed in the analysis outputs, substantial session-to-session variability can influence trend detection and consistency checks. In scenarios where data is noisy, sparse, or incomplete, the agent may produce misleading interpretations or false-positive alerts, thereby affecting the reliability of its recommendations. 

Furthermore, despite demonstrating accurate summarization and contextual reasoning, large language models are known to carry an inherent risk of hallucination, whereby generated responses may include information not grounded in the source data. Although structured tool invocation and data-grounded prompting were employed, continued use of retrieval-augmented generation (RAG) guardrails and validation mechanisms is necessary to further mitigate this risk.

### Future Work

Building on the identified limitations, several avenues for future work are proposed to extend and strengthen the findings of this study. 
First, given that the AI agent’s analytical accuracy is dependent on the quality of the underlying performance data, future research will focus on data quality enhancement mechanisms. Integrating preprocessing and validation layers would reduce the likelihood of false-positive interpretations and improve the robustness of trend detection and recommendation generation. 

Second, to further mitigate the risk of hallucination in large language model outputs, future work will expand the use of retrieval-augmented generation (RAG) and verification guardrails. This may include stricter grounding constraints, response validation against source data, and ensemble verification strategies where analytical outputs are cross-checked against deterministic statistical computations. Additionally, evaluating alternative or fine-tuned domain-specific language models may further improve factual accuracy. 

Finally, future extensions will explore advanced predictive and learning-based models for performance forecasting, including time-series and machine learning approaches, and assess their integration alongside explainable AI techniques. Longitudinal studies involving extended athlete cohorts and real-world deployment will also be conducted to evaluate system effectiveness, user trust, and decision impact over time.


### Acknowledgements
I greatly appreciate Al Kafri Ala and Michael Lawson, for their invaluable guidance, constructive feedback, and unwavering support throughout the course of research.

By ~ *Confidence Antwi*

ENJOY!!