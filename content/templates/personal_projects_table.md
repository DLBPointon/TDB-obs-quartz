<%*
const dv = app.plugins.plugins.dataview.api;

const table = dv.markdownTable(["File", "Date", "Description","Type", "Status"], dv.pages("#Personal")
		.sort(b => b.date)
		.sort(b => b.file.name)
		.map(b => [b.file.link, b.date_started, b.description, b.type, b.status]))
%>

<%table%>