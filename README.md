# Monthly-Calendar
<!DOCTYPE html>
<html>
<head>
  <title>Cultural Festival Calendar</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>🎉 Cultural Festival Calendar</h1>
  <div id="calendar"></div>
  <script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>
  <script>
    const csvUrl = 'festivals.csv'; // Path to your CSV

    fetch(csvUrl)
      .then(response => response.text())
      .then(csv => {
        const data = Papa.parse(csv, { header: true }).data;
        const calendarDiv = document.getElementById('calendar');

        data.forEach(event => {
          const div = document.createElement('div');
          div.className = 'event';
          div.innerHTML = `
            <strong>${new Date(event.Date).toDateString()}</strong><br/>
            <span>${event.Name}</span><br/>
            <em>${event.Description || ''}</em>
          `;
          calendarDiv.appendChild(div);
        });
      });
  </script>
</body>
</html>
body {
  font-family: sans-serif;
  padding: 2rem;
  background-color: #fffaf0;
}
#calendar {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.event {
  background-color: #fffbe6;
  border: 1px solid #f0c040;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 2px 2px 6px #ddd;
}
