---
time: 2025-05-05 00:00
topics: fdsdfds
Created: <% tp.date.now("YYYY-MM-DD HH:MM") %>
Modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:MM") %>
aliases:
tags:
---

<%* let title = tp.file.title
if (title.startsWith("Untitled")) { 
  title = await tp.system.prompt("Title"); 
  await tp.file.rename(title); 
}

tR += "---" 
%>

# <%* tR += title %> 

<% tp.file.cursor(1) %>

# 📍Location
Date:
Time:
Location:

# 🧑‍🧑‍🧒 Participants
- firstName LastName
# 🗓️ Agenda
| Time  | Topic |
| ----- | ----- |
| xx:xx |       |

# ✔️ Action Items
- [ ] item1

---
time: 00:00
topics: fdsdfds
---


