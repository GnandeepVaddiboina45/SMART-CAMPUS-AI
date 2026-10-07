# Smart Campus AI

AI-powered campus assistant for the PBL Hackathon Expo (Problem 20).

## Features
- **AI Assistant**: RAG-style answers from the campus database (timetable, events, facilities, faculty, resources), shows sources, never invents data.
- **Chat system**: new chat, history, rename, delete, clear, search, voice input.
- **Student dashboard**: today's timetable, next class, events, announcements, quick search.
- **Faculty Management Panel**: Add / Edit / Delete / Search / Filter / Paginate for 12 sections, delete confirmation.
- **Roles**: Student = read-only, Faculty = full management.
- **Dark / light mode**, responsive layout.

## Files
| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + JS, single file) |
| `seed-data.json` | Demo college data (replace with your real data) |

## Important: how it runs
`index.html` was built for the **Claude Artifacts runtime**. Its database (`window.claude` db),
user roles (`user`) and AI (`sample`) come from claude.ai, so it works when published as a
Claude artifact. If you host it on GitHub Pages as-is, it will show a
"please open signed in" message because those services do not exist outside claude.ai.

To run it standalone on GitHub Pages, replace the three calls in `init()` and the db/AI
code with Supabase + an LLM API (tables: users, student_profiles, faculty_profiles,
departments, classrooms, timetable, events, announcements, academic_resources,
campus_facilities, campus_locations, faqs, ai_knowledge, chat_conversations, chat_messages,
with Row Level Security: faculty = full CRUD, students = SELECT only).

## Roles (in the Claude version)
Faculty = people with edit access to the artifact. Students = viewers (read-only).

## Tech
HTML, CSS, vanilla JavaScript, keyword + intent retrieval (RAG-style), LLM for answer wording.
