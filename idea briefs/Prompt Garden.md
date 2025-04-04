### Misc. Prompts
**Initiatialization:**
```
I would like to make a simple app called "Prompt Garden" that allows me to create and manage LMM prompts for various projects. The audience will be primarily me, though other colleagues will likely use this too.

I will go into more detail on the specific functionality of this app in future prompts, but for now I want to build a solid and reliable foundation for this application.  
  
The stack should be extremely simple, with  
react/nextjs/chadcn/tailwind on the front-end and a simple google sheets backend. I want to start with a completely blank slate, do not attempt to make any interface unless instructed.
  
For now, let's focus on setting up the front-end foundation of this project and continually perfecting the overall UI/UX before we hook it up to a backend (which will eventually be a Google Sheet).
```

**Structure:**
```
Excellent, let's talk about the structure for this site. It should have a "Home" page and a "Detail" page for prompts. There should also be a "Add Prompt" page that allows me to add a new prompt.

On the homepage, there should be a search bar and a list of cards that contain prompt content. I should be able to click into a prompt to see a detail page.
```


**App Requirements:**
- Search for Prompts
- Make New Prompts
- Manage Prompts
	- Edit/Delete (by navigating to a Sheets DB and highlighting the line)
- Google Sheets Database
- Edit Prompts (by navigating to a Sheets DB and highlighting the line)
- Delete Prompts

### Data Model
```JSON
{
  // Unique identifier for the prompt
  // Type: String
  // Used for: Database references, URLs (e.g., /prompt/1), and ensuring uniqueness
  "id": "1",

  // Display name of the prompt
  // Type: String
  // Used for: UI display, search functionality, and organization
  "title": "Blog Post Writer",

  // The core prompt text without any special markup
  // Type: String
  // Used for: The primary instruction or prompt content
  "mainContent": "Write a blog post about AI",

  // Array of context notes, stored as a JSON string
  // Type: Stringified JSON Array of ContextNote objects
  // Format: Each object has { content: string, position: string }
  // Used for: Additional instructions or notes that supplement the main content
  "contexts": "[{\"content\": \"Make sure to include recent developments\", \"position\": \"after-first-paragraph\"}]",

  // Array of follow-up prompts, stored as a JSON string
  // Type: Stringified JSON Array of FollowUp objects
  // Format: Each object has { content: string, index: number }
  // Used for: Sequential or related prompts that should be executed after the main prompt
  "followUps": "[{\"content\": \"Now create a summary\", \"index\": 1}, {\"content\": \"Generate social media posts\", \"index\": 2}]",

  // Array of categorization tags, stored as a JSON string
  // Type: Stringified JSON Array of strings
  // Used for: Filtering, categorization, and organization of prompts
  "tags": "[\"writing\", \"blog\", \"AI\"]",

  // ISO 8601 timestamp of when the prompt was created
  // Type: String (ISO 8601 datetime)
  // Used for: Record keeping, sorting by creation date
  "createdAt": "2024-04-04T12:00:00Z",

  // ISO 8601 timestamp of the last modification
  // Type: String (ISO 8601 datetime)
  // Used for: Version tracking, sorting by last update
  "updatedAt": "2024-04-04T12:00:00Z"
}
```