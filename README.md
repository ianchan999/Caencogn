# What is Caenocogn

Caenocogn: Caenocogn revolutionizes AI interactions with its intelligent memory layer. By remembering user preferences, adapting to individual needs, and continuously learning, Caenocogn enhances customer experiences and improves the performance of customer support chatbots, AI assistants, and autonomous systems.

## Quick Start

Install the Caenocogn via pip:

```bash
pip install Caenocogn
```

### Basic Usage

Caenocogn is fully reliant on an LLM to operate, with OpenAI's gpt-4o as the standard choice. Nonetheless, it is compatible with a range of LLMs; consult our documentation for more information. [Supported gpt-4o documentation](https://platform.openai.com/docs/models).

<details>
<summary>How to link OPENAI_API_KEY</summary>

```python
import os
os.environ["OPENAI_API_KEY"] = "sk-string of your key"
```
</details>


The following task falls within the scope of your memory operations:

1. Append: Persist a recollection from arbitrary textual data
2. Update: The existing data associated with the given memory ID
3. Query: Retrieve recollections based on a query
4. Fetch: Fetch memories for a certain user/agent/session
5. Historical Analysis: Examine the alterations of a designated memory ID

```python
# 1. Add: Store a memory from any unstructured text
result = m.add("I'm dedicated to refining my football game. Are there any online training programs you would suggest?", user_id="shannon", metadata={"category": "hobbies"})

# Created memory --> 'Improving her football skills.' and 'Searching for online suggestions.'
```

```python
# 2. Update: update the memory
result = m.update(memory_id=<memory_id_1>, data="Regularly plays football on weekends.")

# Updated memory --> 'Likes to play football on weekends.' and 'Searching for online suggestions.'
```

```python
# 3. Search: collect to the memories
related_memories = m.search(query="What activities does Shannon pursue for pleasure?", user_id="shannon")

# Retrieved memory --> 'Likes to play football on weekends'
```

```python
# 4. Get all memories
all_memories = m.get_all()
memory_id = all_memories["memories"][0] ["id"] # get a memory_id

# All memory items --> 'Likes to play football on weekends.' and 'Searching for online suggestions.'
```

```python
# 5. Capture a timeline of memory usage for a designated memory_id
history = m.history(memory_id=<memory_id_1>)

# Logs corresponding to memory_id_1 --> {'prev_value': 'Striving to become a better football player and looking into online football courses.', 'new_value': 'Likes to play football on weekends' }
```
