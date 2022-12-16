<%*
const dv = app.plugins.plugins.dataview.api;

const table = dv.markdownTable(["File", "Date", "Description"], dv.pages("#workbased")
		.sort(b => b.date)
		.map(b => [b.file.link, b.date, b.description]))
%>

<%table%>