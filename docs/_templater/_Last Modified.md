<%*
const editor = app.workspace.activeLeaf.view.editor;
const lineNumber = editor.getCursor().line;
const currentLine = editor.getLine(lineNumber);

// From https://stackoverflow.com/questions/23593052/format-javascript-date-as-yyyy-mm-dd
const offset = (new Date()).getTimezoneOffset() * 60 * 1000;
const now = new Date((new Date()).getTime() - offset);
const newLine = "modified:: " + now.toISOString().substring(0, '2023-01-31T22:33'.length) + "  ";

if (currentLine.startsWith("modified:: ")) {
	editor.setLine(lineNumber, newLine);
} else {
	editor.setLine(lineNumber, currentLine + `\n` + newLine);
}
%>