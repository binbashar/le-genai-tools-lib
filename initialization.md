
---
AI Context and Prompt Engineering



By Exequiel Barrirero

5 min

Add a reaction
Introduction
Generative AI has become an integral part of our system design, powering features from chat assistants to automation agents. To harness these AI models effectively, we rely on prompt engineering and its broader evolution, context engineering. 

Prompt engineering is the craft of writing effective instructions or questions for a language model (help.openai.com). 

rocket MUST check 
AI Context and Prompt Engineering | Leverage Prompt Library

Context engineering takes this a step further – it’s about designing the entire environment or context that the model sees, not just a single prompt. In practice, this means carefully preparing all relevant information (instructions, data, examples, etc.) that we feed into the model so it can produce reliable results. The quality of the AI’s output directly depends on the quality and clarity of the input we provide (oreilly.comoreilly.com).


Prompt Engineering Basics
Prompt engineering is the process of designing and optimizing prompts to guide a language model’s responses (help.openai.com). In simpler terms, it’s how we “program in prose” – by giving the model clear instructions or questions in natural language. A well-crafted prompt can make the difference between a confused, off-target answer and a highly relevant response. Some general best practices for prompt writing include:

Be clear and specific: Ambiguous prompts yield ambiguous answers. Specify exactly what you want, provide necessary context, and avoid vague language (help.openai.com). 

For example, instead of “Summarize this,” ask “Summarize the following incident report focusing on root cause and resolution.”

Define roles or style if needed: We often start a prompt by assigning the model a role or persona.

E.g., “You are an expert DevOps engineer…”. This gives the model context on how to respond (technical tone, level of detail, etc.).

Provide examples (few-shot prompting): When feasible, showing a couple of example inputs and desired outputs can train the model on the pattern you expect. This is useful for formats or complex tasks.

Iterate and refine: Prompt design is usually iterative (help.openai.com). We test a prompt, observe the output, then tweak the wording or add details to fix issues. Even small changes (adding a hint, reordering words) can significantly impact the result.

By following these practices, we’ll managed to craft prompts that elicit more accurate and relevant answers from models. But prompt wording alone isn’t the whole story – we also need to consider context.

From Prompt Engineering to Context Engineering
As our AI use cases grew more complex (multi-step workflows, memory, tool usage), the concept of context engineering has become crucial. Prompt engineering focuses on what we ask the model at a single moment. Context engineering focuses on what information the model has available when we ask it (medium.commedium.com). In other words, prompt engineering is about crafting a good instruction, whereas context engineering is about assembling all the right background knowledge and data around that instruction.

“Prompt Engineering is what you do inside the context window. Context Engineering is how you decide what fills the window.” (medium.com)

warning A simple prompt might work in isolation, but in a realistic setting it could get “drowned in noise” if the model’s context is full of irrelevant or poorly organized information (medium.com). 

check mark button Context engineering means managing the model’s input holistically: we load the context window with just the information the model needs, in a structured way. This can include the user’s query, our carefully written prompt, relevant documents or database results, summaries of prior interactions, and so on (oreilly.comoreilly.com).

Crucially, context engineering frames the whole conversation or task for the AI. It acknowledges that real-world LLM applications require more than a clever one-liner prompt – they require feeding the model all the supporting details so it isn’t “guessing in the dark.” As one expert put it, context engineering is “the art of providing all the context for the task to be plausibly solvable by the LLM” (oreilly.com). 

This discipline involves decisions like: 

Which knowledge base entries or code snippets to retrieve and include? 

How to summarize or truncate history to fit the model’s input limits? 

When to call external tools (and how to feed their output into the prompt)? 

By answering these questions, we create an information pipeline that sets the AI up for success (oreilly.comoreilly.com).

In summary, prompt engineering is a subset of context engineering (medium.com). We still need great prompts, but we also need to control the context around those prompts. Our team’s approach should reflects this: we design not just prompts in isolation, but entire flows of information for the model.

Multi-Agent Prompt Design in Our System
One way we apply context engineering is through a multi-agent architecture. Instead of a monolithic AI handling everything, we have specialized agents with well-defined roles, coordinated by an orchestrator. Each agent has its own prompt (often a concise system message defining its job and constraints), and the orchestrator is responsible for feeding the right context to the right agent at each step. This modular approach helps keep each prompt focused and the overall interaction organized (GitHub).

For example, in our latest GenAI document processing project https://github.com/binbashar/le-genai-ml-dilyConnect your Github account, very similar to whats presented in the Dynamics 365 Pipeline Example the workflow is broken down into stages handled by different agents (Data Fetcher, Analyzer, Recommender, Notifiers, etc.). The orchestrator gathers data and passes it to each agent in turn (GitHub). One of those is a Slack Notifier Agent, whose sole purpose is to send a notification to Slack when called (GitHub). 

Then we wrote a very targeted prompt for this agent that prevents it from doing anything except the notification task. Here is an excerpt of that system prompt:

Slack Notifier Agent Prompt (excerpt): “You are a Slack Notifier Agent. Your single job is to send Slack messages via the slack_notify action. Do not read from Slack, do not start conversations, and do not summarize chat history. When the user asks you to notify someone or a channel, you compose a concise message and call the tool.”

This prompt encapsulates the agent’s role & boundaries. It explicitly instructs the model to only perform the Slack messaging operation and nothing else. By engineering the prompt this way, we ensure the agent remains focused (it won’t, say, try to have a back-and-forth chat or attempt to summarize previous messages). All it will do is format a Slack message and invoke the Slack API tool. This is a prime example of prompt engineering for a specific context: the context here is that the agent is invoked purely as a notifier with a prepared message, so we strip away any other conversational or analytical duties from its instructions.

This modular, context-focused design has several benefits:

 First, each agent’s prompt can be simpler and clearer since it only deals with one slice of the task. 

Second, the orchestrator can manage the high-level flow, injecting the right data into each agent’s context. 

For instance, the Action Recommender Agent in the pipeline receives a prompt along with curated input: it’s given the CRM data, external signals, and analysis results, and its prompt likely says something like “Given the following account info, produce 2-3 recommended actions…”. The orchestrator ensures that agent gets exactly that relevant info and nothing extraneous. This way, the recommender’s prompt + context are engineered together to yield useful suggestions without distraction. The Slack agent then just takes the final recommendation and sends it out, with its own strict prompt to not add anything beyond the message. Each agent thus operates within a tailored context bubble.

In essence, our system is practicing context engineering by dividing responsibilities. We engineer the context for each agent (via the orchestrator and carefully written prompts) so that the agent can do its job accurately and efficiently. This approach reduces confusion and makes the overall AI behavior more predictable. It’s a scalable strategy, because we can add or update agents and their prompts independently as our needs evolve.

eg: Equivalent to what we’re doing here with claude code sub-agents and cmds: le-tf-infra-aws/.claude at master · binbashar/le-tf-infra-aws 

Leverage Prompt Library
In conclusion, context and prompt engineering are key to building reliable AI-driven features in our systems. We’ve learned that providing clear instructions to the model (prompt engineering) and assembling the right information around those instructions (context engineering) go hand in hand to yield the best results. Our use of focused agent prompts and orchestrated context in our implementations is a practical showcase of these principles. 

By establishing a Leverage Prompt Library: 
AI Prompt Library and Template Catalog, we are codifying this knowledge for the team – creating a reference that captures what works and why, and that can evolve as we experiment with new models and techniques.
---
AI Prompt Library and Template Catalog

By Exequiel Barrirero

4 min

Add a reaction
TODO:  Initialize binbash Leverage GitHub repo for prompts: binbashar/le-genai-prompt-lib, in oder to easily browsed and even queried by AI tools in the future, as opposed to siloed knowledge. (@Diego Ojeda @Alex de los Santos @Ignacio Gómez @luis.gallardo)

As we develop more prompts for various agents and use cases, maintaining them in a structured way becomes important. We are thinking on a Prompt Library – a catalog of prompt templates and examples – to capture our collective prompt engineering knowledge. The idea is to have a central place where we document each prompt’s details and context, so that we can reuse successful patterns and avoid “reinventing the prompt” for similar tasks in the future. This library will also help new team members learn from past prompt designs and understand the rationale behind them.


References & Inspiration: Community prompt collections like:

Repos:  these repositories provide a variety of example prompts for different roles and tasks, which helped spark ideas for our own prompts. However, our internal library will be tailored to our specific use cases and products, and we’ll enrich each entry with the metadata mentioned above (which is something the general “awesome” lists typically lack)

https://github.com/langgptai/awesome-claude-prompts 

https://github.com/abilzerian/LLM-Prompt-Library  

https://github.com/f/awesome-chatgpt-prompts 

 https://github.com/ai-boost/awesome-prompts 

Guides and Articles

OpenAI’s guide on prompt best practices (help.openai.com) 

Articles on context engineering (oreilly.commedium.com)  informed our approach and underscore industry best practices. 


Each entry in the prompt library will include metadata to give the prompt context. We plan to record information such as:

Prompt Name/Purpose: What the prompt is for, e.g. “Slack Notification Agent” or “Account Briefing Generator”.

Project or Workflow Context: Where or how it’s used in our systems (for example, “Dynamics Pipeline – Notification stage” or “Leverage CLI – Terraform module helper”).

Prompt Template: The actual text of the prompt (or a template with placeholders), including any role instructions and example inputs/outputs if applicable.

Key Design Notes: Important aspects of the prompt engineering – e.g. “uses a strict system role to limit scope,” “provides step-by-step examples,” “asks for JSON output,” or particular phrasings that improved performance.

Effectiveness/Results: Any observations about how well it works. For instance, does this prompt reliably achieve the desired outcome? Were there any known failure modes or needed tweaks? (Over time, we can update this as we refine prompts or test them on new models.)

Related Prompts or Tools: Links to similar prompts in the library or references to external prompt examples that inspired it.

By capturing these details, the library entry serves as both documentation and a template that can be adapted to new scenarios. For example, if we later need a Teams Notifier Agent, we could copy the Slack prompt entry and adjust it, rather than starting from scratch.


Use Cases Across Our Projects
We anticipate creating and cataloging prompts across several domains of our platform, aligning with key projects:

keycap: 1 Reference Architectures (https://github.com/binbashar/le-tf-infra-aws) – Our best-practice AWS architecture library (e.g. Landing Zones, Data Lake, GenAI stack). 

We might develop prompts to explain a reference architecture in simple terms, or an agent that can answer questions about the architecture choices. 

For instance, a prompt could guide an AI to “Act as a cloud architect and describe the VPC setup for our Data Lake blueprint.” Such a prompt would need context about the reference design to produce correct answers.


keycap: 2 Infrastructure-as-Code (IaC) Library (Overview - binbash Leverage™) – Our Terraform/OpenTofu modules. 

Potential prompts here include ones to assist in code generation or validation. 

For example, we could have a prompt that helps generate a Terraform/OpenTofu snippet given high-level input (like “I need an S3 bucket with encryption and versioning”) or an agent that reviews a Terraform plan for policy compliance. 

These prompts must be engineered with context about our module standards and output format.


keycap: 3 Leverage CLI (https://github.com/binbashar/leverage ) – Our CLI tool for environment management and scaffolding. 

We envision prompts that could be integrated into the CLI as smart assistants. 

One idea is a CLI command that, behind the scenes, uses an LLM prompt to bootstrap IaC configurations or compose CLI commands based on a user’s natural language request. 

For example, a user might say “create a new dev environment with a demo web app,” and an AI agent with a prompt could translate that into a sequence of CLI and OpenTofu/Terraform actions. The prompt for that agent would have to capture the user’s intent and map it to our CLI syntax, with knowledge of the project structure – a non-trivial context engineering challenge!


keycap: 4 Leverage Documentation (binbash Leverage™ - Home) – Our comprehensive docs portal and knowledge base. 

Here, prompts can help with documentation Q&A or content generation. 

We could deploy a doc chatbot whose prompt is engineered to use our documentation pages as context (via retrieval). In the prompt library, we’d document something like “Docs QA Assistant” with details on how it cites sources and stays factual (for example, instructions to only use info from provided docs and a style guideline for answers). 

Another use case is generating release notes or summary reports from raw text – a prompt that instructs an AI to convert a changelog into a polished announcement, for instance.

Each of these areas will have its unique prompts, but by storing them in a unified library, we can maintain consistency. For example, if both the Reference Architecture assistant and the Docs QA bot need a similar tone or compliance with our content guidelines, we can ensure their prompts reflect that. Reusability will also save time: a well-crafted prompt for summarizing technical content can likely be reused or adapted for different projects.

Next Steps 
Going forward, we will continue to refine our prompts (e.g. tuning them for different model versions like Anthropic Claude vs. OpenAI GPT-5) and update the library accordingly. 

We encourage team members to contribute to the prompt catalog: whenever you develop a new prompt (or improve an existing one), document it in the library with its context and lessons learned. Not only will this help others facing similar tasks, but it will also allow us to systematize prompt engineering as a discipline within our projects rather than treat it as ad-hoc magic.

By treating prompts and context as first-class design elements – much like we design code modules or API interfaces – we bring engineering rigor to our AI solutions. This will be increasingly important as we scale up our GenAI capabilities. With a solid foundation in context and prompt engineering, and a knowledge base of tried-and-true prompt templates, we’ll be well-equipped to build AI features that are robust, transparent, and reuseable across the organization.

We will continue to draw on such resources while focusing on our unique context as we expand the prompt library.

---
