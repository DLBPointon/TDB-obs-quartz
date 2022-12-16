<%*
const dv = app.plugins.plugins.dataview.api;

const table = dv.markdownTable(["File", "Date", "Description","Type", "KSBs"], dv.pages("#portfolio")
		.sort(b => b.date)
		.map(b => [b.file.link, b.date, b.description, b.type, b.KSBs]))
%>

<%table%>