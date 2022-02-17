<%* await tp.file.move("/Adventure Notes/") %>

<%*
let index = tp.config.target_file.parent.children
  .filter(page => page.name.includes("Session"))
  .reduce((acc, curr) => {
    let ending = curr.basename.slice(curr.basename.lastIndexOf("Session ") + 8);
    console.log(curr.basename, ending);
    return (ending >= acc && !isNaN(ending)) ? Number(ending) + 1 : acc;
  }, 1);
console.log(index);
%>

<%* await tp.file.rename(`${tp.date.now()} - Session ${index}`); %>

tags: #session

---

# Session <% tp.file.name %>
