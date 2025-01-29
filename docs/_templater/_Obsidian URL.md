<%*
const activeEditor = app.workspace.activeLeaf.view.editor;

// Get the text of the active editor
const editorText = activeEditor.getValue();

function getObsidianLink(oldLink){
  const splitLink = oldLink.split('|');
  let linkTarget = splitLink[0];
  let linkText = splitLink.length == 1 ? linkTarget : splitLink[1];
  
  if (linkTarget[0] == '#') {
    linkText = linkText[0] == '#' ? linkText.substring(1) : linkText;
    return `[${linkText}](${linkTarget})`;
  }

  // If the link points to a heading in another document, remove that part,
  // as it cannot be rendered as an Obsidian URL.
  linkTarget = linkTarget.split('#')[0];

  // We need to full path to the Link Target.
  // DataView can answer that question.
  const obsidianLink = `[${linkText}](obsidian://open?file=${encodeURI(linkTarget)})`;
  return obsidianLink;
}

// Find all the link matches in the editor text
const linkRegex = /(?<=[^!])\[\[([^\]]+)\]\]/g;
let replacements = [];
let match;
while ((match = linkRegex.exec(editorText))) {
  // Get the components of the link, which can be [[Article]] or [[Article|Alias]]
  const oldLink = match[1];
  const obsidianLink = getObsidianLink(oldLink);

  // Get the line number and position of the link
  const cursorStart = {
    line: 0,
    ch: match.index
  }
  const cursorEnd = {
    line: 0,
    ch: match.index + match[0].length
  }
  replacements.push({
    oldText1: match[0],
    oldText2: match[1],
    newText: obsidianLink,
    start: cursorStart,
    end: cursorEnd
  });
}

// Replace in reverse order, otherwise the positions no longer match.
replacements.reverse();
replacements.forEach(replacement => {
  activeEditor.replaceRange(replacement.newText, replacement.start, replacement.end);
});
%>