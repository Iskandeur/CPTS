The goal of this repository is to store important information, or any stuff I find interesting in my CPTS journey.

See [[FORMATTING]] for documentation standards.

## Structure

This vault uses an object-based structure. Each note represents a specific concept, tool, technique, or process related to penetration testing.
Files about meta-topics (such as formatting) have their name capslocked.

Key starting points:

- [[Penetration Testing Process]] - Overview of the stages.
- [[Information Security (Infosec)]] - Foundational concepts.
- [[Laws and Regulations (Cybersecurity)]] - Legal and ethical context.

## Vault Restructuring Plan (Completed)

The vault has been restructured based on user request. The goal was to move from a chapter-based organization to an **object-based structure**.

This means creating dedicated notes for individual concepts, tools, techniques, or entities (e.g., `Ports.md`, `Nmap.md`, `Scope Questionnaire.md`, `Active Directory.md`, `Kerberos.md`, etc.).

**Benefits:**

*   **Granularity:** Easier to find and update specific pieces of information.
*   **Incremental Learning:** Facilitates adding details to the correct note as they are learned, rather than just copying large chunks.
*   **Linking:** Encourages linking related concepts together, building a knowledge graph.

**Process:**

1.  Identify key objects/concepts from the existing notes and the formation material.
2.  Create new markdown files for each object.
3.  **Migrate relevant information from the old structure to the new object files, ensuring existing data finds its place.**
4.  **Interlink related concepts using Obsidian's `[[WikiLink]]` format.**
5.  Update old links if necessary.

This approach aims to make the vault a more dynamic and useful personal knowledge base throughout the CPTS journey.

## Vault Improvement Suggestions

Based on the current structure and goals, here are some suggestions for enhancing the vault:

1.  **Centralized Hubs/MOCs (Maps of Content):**
    *   **Suggestion:** Create more "Map of Content" (MOC) notes to act as curated indexes for broader topics (e.g., `[[Networking MOC]]`, `[[Web Security MOC]]`, `[[Active Directory MOC]]`). Link related concept notes from these MOCs.
    *   **Meta-Suggestion:** Periodically review topics that could benefit from a dedicated MOC to improve navigation.

2.  **Tagging Strategy:**
    *   **Suggestion:** Develop a systematic tagging strategy (e.g., `#tool/nmap`, `#concept/networking`, `#status/stub`) beyond just `#new`.
    *   **Meta-Suggestion:** Define the tagging system (perhaps in `FORMATTING.md` or `TAGGING.md`) for consistency. Start simple and refine as needed.

3.  **Templates:**
    *   **Suggestion:** Use Obsidian's templating features for standard structures in common note types (e.g., Tool, Technique, Vulnerability notes).
    *   **Meta-Suggestion:** Start with simple templates and add complexity only when clearly beneficial.

4.  **External Resources & Annotations:**
    *   **Suggestion:** When linking external resources, briefly summarize their relevance or key takeaway for context. Consider web clipping or PDF annotation tools if integrating many external articles.
    *   **Meta-Suggestion:** Decide on a consistent style for referencing external links.

5.  **Visualizations (Graph View):**
    *   **Suggestion:** Regularly use Obsidian's graph view (global and local) to identify isolated notes or potential connections between concepts.
    *   **Meta-Suggestion:** Actively use the graph view to ask questions about the knowledge structure.

6.  **Review and Refinement Cycle:**
    *   **Suggestion:** Schedule periodic reviews to tidy up notes, add links, flesh out stubs, and refactor structure.
    *   **Meta-Suggestion:** Treat the vault like a garden requiring regular tending. Embrace incremental improvement.

7.  **Capture Workflow:**
    *   **Suggestion:** Define a clear process for capturing new information (e.g., daily notes, inbox note).
    *   **Meta-Suggestion:** Optimize the capture workflow for speed and low friction to encourage consistent use.