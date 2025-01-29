<%*
const editor = app.workspace.activeLeaf.view.editor;
const line = editor.getLine(editor.getCursor().line);
const txt = ((line == '- ') ? 'relates_to:: ' : '- relates_to:: ');
const newline = ((line == '- ') ? '' : '\n');
%><% txt %>[[<% tp.file.cursor(1) %>]]<% newline %>