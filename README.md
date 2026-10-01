<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Career Planning Job Application</title>
  <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <style>
    :root {
      --navy: #003366;
      --yellow: #FFD300;
      --white: #ffffff;
      --text: #111111;
      --muted: #5a5a5a;
      --card-bg: #ffffff;
      --shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
      --border: #dfe3e8;
      --danger: #b10000;
      --soft: #f6f8fb;
    }

    * { box-sizing: border-box; }
    html, body, #root { margin: 0; min-height: 100%; font-family: Arial, sans-serif; background: var(--white); color: var(--text); }
    body { padding: 18px; }

    .app-shell {
      max-width: 980px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    .card {
      background: var(--card-bg);
      border-radius: 12px;
      padding: 18px 18px 20px;
      box-shadow: var(--shadow);
      border: 1px solid rgba(0,0,0,0.03);
    }

    .topbar {
      background: var(--navy);
      color: white;
      padding: 18px 18px 14px;
    }

    .header-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 12px;
    }

    h1 {
      margin: 0;
      font-size: clamp(1.4rem, 2.1vw, 2rem);
      letter-spacing: 0.2px;
    }

    .button-row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      align-items: center;
    }

    button {
      background: var(--yellow);
      color: #042b4e;
      border: none;
      border-radius: 8px;
      padding: 9px 13px;
      font-size: 0.96rem;
      font-weight: 700;
      cursor: pointer;
      box-shadow: 0 2px 6px rgba(0,0,0,0.12);
    }

    button.secondary {
      background: transparent;
      color: white;
      border: 1px solid rgba(255,255,255,0.25);
      box-shadow: none;
    }

    .progress-wrap {
      display: flex;
      flex-direction: column;
      gap: 9px;
    }

    .progress-meta {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      flex-wrap: wrap;
      font-size: 0.92rem;
      color: rgba(255,255,255,0.95);
    }

    .progress-bar {
      position: relative;
      width: 100%;
      height: 16px;
      background: rgba(255,255,255,0.14);
      border-radius: 999px;
      overflow: hidden;
      border: 1px solid rgba(255,255,255,0.1);
    }

    .progress-fill {
      height: 100%;
      width: 0%;
      background: var(--yellow);
      border-radius: inherit;
      transition: width 0.45s ease;
    }

    .progress-percent {
      min-width: 56px;
      text-align: right;
      font-weight: 700;
      color: white;
    }

    .section-title {
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--navy);
      margin-bottom: 12px;
    }

    .form-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }

    .field-col { display: flex; flex-direction: column; gap: 10px; }

    .field {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    label {
      font-size: 0.95rem;
      font-weight: 600;
      color: #222;
    }

    input[type="text"],
    input[type="email"],
    input[type="tel"],
    input[type="date"],
    textarea {
      width: 100%;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px 12px;
      font-size: 1rem;
      background: white;
      color: #111;
    }

    textarea {
      min-height: 120px;
      resize: vertical;
    }

    input:focus, textarea:focus {
      outline: none;
      border-color: var(--navy);
      box-shadow: 0 0 0 3px rgba(0, 51, 102, 0.08);
    }

    .radio-block {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .radio-row {
      display: flex;
      gap: 18px;
      align-items: center;
      flex-wrap: wrap;
      font-weight: 600;
    }

    .radio-row label {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-weight: 600;
    }

    .help-box {
      background: var(--soft);
      border-left: 4px solid var(--navy);
      color: #1b3151;
      padding: 10px 12px;
      border-radius: 8px;
      font-size: 0.96rem;
      line-height: 1.45;
    }

    .references-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 12px;
    }

    .reference-card {
      background: linear-gradient(180deg, #fff, #fcfcfc);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.04);
    }

    .reference-card h3 {
      margin: 0 0 10px;
      font-size: 1rem;
      color: var(--navy);
    }

    .error {
      font-size: 0.86rem;
      color: var(--danger);
      margin-top: -2px;
      font-weight: 600;
    }

    .footer-note {
      background: #f9fafb;
      border: 1px solid var(--border);
      font-size: 0.92rem;
      color: var(--muted);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .print-only { display: none; }

    @media (max-width: 760px) {
      .form-grid, .references-grid {
        grid-template-columns: 1fr;
      }
      .header-row {
        flex-direction: column;
        align-items: flex-start;
      }
      .button-row {
        width: 100%;
      }
      button {
        flex: 1 1 auto;
      }
    }

    @media print {
      body { padding: 0; }
      .no-print { display: none !important; }
      .card {
        box-shadow: none;
        border: 1px solid #2d2d2d;
        page-break-inside: avoid;
      }
      .topbar {
        background: white !important;
        color: black !important;
        border: none !important;
        box-shadow: none !important;
      }
      .topbar .progress-bar, .topbar .progress-percent { display: none !important; }
      .progress-meta { color: black !important; }
      .section-title { color: black !important; }
      * { color: black !important; }
      .print-only { display: block; }
    }
  </style>
</head>
<body>
  <div id="root"></div>

  <script type="text/babel" data-presets="react">
    const STORAGE_KEY = "career-app-data-v1";

    const defaultState = {
      personal: {
        fullName: "",
        date: "",
        address: "",
        city: "",
        state: "",
        zip: "",
        phone: "",
        email: ""
      },
      job: {
        position: "",
        desiredStart: "",
        employmentType: ""
      },
      education: {
        schoolName: "",
        expectedGrad: ""
      },
      work: {
        employer: "",
        jobTitle: "",
        supervisor: "",
        startDate: "",
        endDate: "",
        startSalary: "",
        endSalary: "",
        responsibilities: ""
      },
      additional: {
        employedBefore: "",
        authorizedToWork: "",
        driversLicense: "",
        militaryService: "",
        convictedFelony: "",
        felonyExplanation: ""
      },
      references: [
        { name: "", relationship: "", phone: "", email: "" },
        { name: "", relationship: "", phone: "", email: "" },
        { name: "", relationship: "", phone: "", email: "" }
      ],
      certification: {
        signature: "",
        date: ""
      }
    };

    function loadSavedData() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        return raw ? JSON.parse(raw) : null;
      } catch (e) {
        return null;
      }
    }

    function countCompletedFields(data) {
      let total = 0;
      let done = 0;

      Object.values(data.personal).forEach(v => {
        total++;
        if (String(v).trim() !== "") done++;
      });

      total += 3;
      if (data.job.position.trim() !== "") done++;
      if (data.job.desiredStart.trim() !== "") done++;
      if (data.job.employmentType.trim() !== "") done++;

      total += 2;
      if (data.education.schoolName.trim() !== "") done++;
      if (data.education.expectedGrad.trim() !== "") done++;

      Object.values(data.work).forEach(v => {
        total++;
        if (String(v).trim() !== "") done++;
      });

      total += 5;
      ["employedBefore", "authorizedToWork", "driversLicense", "militaryService", "convictedFelony"].forEach(k => {
        if (String(data.additional[k]).trim() !== "") done++;
      });

      if (data.additional.convictedFelony === "Yes") {
        total++;
        if (String(data.additional.felonyExplanation).trim() !== "") done++;
      }

      total += 12;
      data.references.forEach(ref => {
        if (ref.name.trim() !== "") done++;
        if (ref.relationship.trim() !== "") done++;
        if (ref.phone.trim() !== "") done++;
        if (ref.email.trim() !== "") done++;
      });

      total += 2;
      if (data.certification.signature.trim() !== "") done++;
      if (data.certification.date.trim() !== "") done++;

      const percent = total === 0 ? 0 : (done / total) * 100;
      return { total, done, percent };
    }

    function formatTimestamp(dateValue) {
      const date = new Date(dateValue);
      return new Intl.DateTimeFormat(undefined, {
        year: "numeric",
        month: "short",
        day: "numeric",
        hour: "numeric",
        minute: "2-digit"
      }).format(date);
    }

    function App() {
      const initial = React.useMemo(() => loadSavedData() || defaultState, []);
      const [form, setForm] = React.useState(initial);
      const [lastSaved, setLastSaved] = React.useState(new Date());
      const [errors, setErrors] = React.useState({});

      const progress = React.useMemo(() => countCompletedFields(form), [form]);
      const percent = Math.round(progress.percent);

      React.useEffect(() => {
        try {
          localStorage.setItem(STORAGE_KEY, JSON.stringify(form));
          setLastSaved(new Date());
        } catch (e) {
          console.error("Save failed", e);
        }
      }, [form]);

      React.useEffect(() => {
        const nextErrors = {};
        const email = form.personal.email.trim();
        if (email && !/^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/.test(email)) {
          nextErrors.email = "Please enter a valid email address.";
        }

        const phoneDigits = form.personal.phone.replace(/\\D/g, "");
        if (form.personal.phone.trim() && phoneDigits.length < 10) {
          nextErrors.phone = "Please enter a valid phone number.";
        }

        const zip = form.personal.zip.trim();
        if (zip && !/^\\d{5}(-\\d{4})?$/.test(zip)) {
          nextErrors.zip = "Please enter a valid ZIP code.";
        }

        setErrors(nextErrors);
      }, [form.personal]);

      function updateSection(section, key, value) {
        setForm(prev => ({
          ...prev,
          [section]: {
            ...prev[section],
            [key]: value
          }
        }));
      }

      function updateReference(index, field, value) {
        setForm(prev => {
          const refs = [...prev.references];
          refs[index] = { ...refs[index], [field]: value };
          return { ...prev, references: refs };
        });
      }

      function handleClear() {
        const confirmed = window.confirm("Are you sure you want to clear all saved information?");
        if (!confirmed) return;
        localStorage.removeItem(STORAGE_KEY);
        setForm(defaultState);
        setLastSaved(new Date());
      }

      function handlePrint() {
        window.print();
      }

      return (
        <div className="app-shell">
          <header className="topbar card">
            <div className="header-row">
              <div>
                <h1>Career Planning Job Application</h1>
              </div>

              <div className="button-row no-print">
                <button type="button" onClick={handlePrint}>Print Application</button>
                <button type="button" className="secondary" onClick={handleClear}>Clear Form</button>
              </div>
            </div>

            <div className="progress-wrap">
              <div className="progress-meta">
                <div className="progress-bar">
                  <div className="progress-fill" style={{ width: percent + "%" }} />
                </div>
                <div className="progress-percent">{percent}%</div>
              </div>

              <div className="progress-meta">
                <div>Progress Saved Automatically</div>
                <div>Last Saved: {formatTimestamp(lastSaved)}</div>
              </div>
            </div>
          </header>

          <main className="card">
            <div className="section-title">Section 1: Personal Information</div>
            <div className="form-grid">
              <div className="field-col">
                <div className="field">
                  <label htmlFor="fullName">Full Name</label>
                  <input id="fullName" type="text" value={form.personal.fullName} onChange={e => updateSection("personal", "fullName", e.target.value)} />
                </div>

                <div className="field">
                  <label htmlFor="date">Date</label>
                  <input id="date" type="date" value={form.personal.date} onChange={e => updateSection("personal", "date", e.target.value)} />
                </div>

                <div className="field">
                  <label htmlFor="address">Mailing Address</label>
                  <input id="address" type="text" value={form.personal.address} onChange={e => updateSection("personal", "address", e.target.value)} />
                </div>

                <div className="field">
                  <label htmlFor="city">City</label>
                  <input id="city" type="text" value={form.personal.city} onChange={e => updateSection("personal", "city", e.target.value)} />
                </div>
              </div>

              <div className="field-col">
                <div className="field">
                  <label htmlFor="state">State</label>
                  <input id="state" type="text" value={form.personal.state} onChange={e => updateSection("personal", "state", e.target.value)} />
                </div>

                <div className="field">
                  <label htmlFor="zip">Zip Code</label>
                  <input id="zip" type="text" value={form.personal.zip} onChange={e => updateSection("personal", "zip", e.target.value)} />
                  {errors.zip && <div className="error">{errors.zip}</div>}
                </div>

                <div className="field">
                  <label htmlFor="phone">Phone Number</label>
                  <input id="phone" type="tel" value={form.personal.phone} onChange={e => updateSection("personal", "phone", e.target.value)} />
                  {errors.phone && <div className="error">{errors.phone}</div>}
                </div>

                <div className="field">
                  <label htmlFor="email">Email Address</label>
                  <input id="email" type="email" value={form.personal.email} onChange={e => updateSection("personal", "email", e.target.value)} />
                  {errors.email && <div className="error">{errors.email}</div>}
                </div>
              </div>
            </div>
          </main>

          <section className="card">
            <div className="section-title">Section 2: Job Details</div>
            <div className="form-grid">
              <div className="field-col">
                <div className="field">
                  <label htmlFor="position">Position Applying For</label>
                  <input id="position" type="text" value={form.job.position} onChange={e => updateSection("job", "position", e.target.value)} />
                </div>

                <div className="field">
                  <label htmlFor="desiredStart">Desired Start Date</label>
                  <input id="desiredStart" type="date" value={form.job.desiredStart} onChange={e => updateSection("job", "desiredStart", e.target.value)} />
                </div>
              </div>

              <div className="field-col">
                <div className="radio-block">
                  <label>Employment Type</label>
                  <div className="radio-row">
                    <label><input type="radio" name="employmentType" value="Full Time" checked={form.job.employmentType === "Full Time"} onChange={e => updateSection("job", "employmentType", e.target.value)} /> Full Time</label>
                    <label><input type="radio" name="employmentType" value="Part Time" checked={form.job.employmentType === "Part Time"} onChange={e => updateSection("job", "employmentType", e.target.value)} /> Part Time</label>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section className="card">
            <div className="section-title">Section 3: Education</div>
            <div className="help-box">
              If you are currently in high school, list your current school and expected graduation date.
            </div>
            <div className="form-grid" style={{ marginTop: 14 }}>
              <div className="field">
                <label htmlFor="schoolName">School Name</label>
                <input id="schoolName" type="text" value={form.education.schoolName} onChange={e => updateSection("education", "schoolName", e.target.value)} />
              </div>

              <div className="field">
                <label htmlFor="expectedGrad">Expected Graduation Date</label>
                <input id="expectedGrad" type="date" value={form.education.expectedGrad} onChange={e => updateSection("education", "expectedGrad", e.target.value)} />
              </div>
            </div>
          </section>

          <section className="card">
            <div className="section-title">Section 4: Work Experience</div>
            <div className="help-box" style={{ marginBottom: 12 }}>
              If you have never had a job, you may use volunteer work, school clubs, sports teams, academic projects, extracurricular activities, or being a high school student.
            </div>

            <div className="field">
              <label htmlFor="employer">Employer / Organization</label>
              <input id="employer" type="text" value={form.work.employer} onChange={e => updateSection("work", "employer", e.target.value)} />
            </div>

            <div className="form-grid" style={{ marginTop: 12 }}>
              <div className="field">
                <label htmlFor="jobTitle">Job Title</label>
                <input id="jobTitle" type="text" value={form.work.jobTitle} onChange={e => updateSection("work", "jobTitle", e.target.value)} />
              </div>

              <div className="field">
                <label htmlFor="supervisor">Supervisor</label>
                <input id="supervisor" type="text" value={form.work.supervisor} onChange={e => updateSection("work", "supervisor", e.target.value)} />
              </div>
            </div>

            <div className="form-grid" style={{ marginTop: 12 }}>
              <div className="field">
                <label htmlFor="startDate">Start Date</label>
                <input id="startDate" type="date" value={form.work.startDate} onChange={e => updateSection("work", "startDate", e.target.value)} />
              </div>

              <div className="field">
                <label htmlFor="endDate">End Date</label>
                <input id="endDate" type="date" value={form.work.endDate} onChange={e => updateSection("work", "endDate", e.target.value)} />
              </div>
            </div>

            <div className="form-grid" style={{ marginTop: 12 }}>
              <div className="field">
                <label htmlFor="startSalary">Starting Salary</label>
                <input id="startSalary" type="text" value={form.work.startSalary} onChange={e => updateSection("work", "startSalary", e.target.value)} />
              </div>

              <div className="field">
                <label htmlFor="endSalary">Ending Salary</label>
                <input id="endSalary" type="text" value={form.work.endSalary} onChange={e => updateSection("work", "endSalary", e.target.value)} />
              </div>
            </div>

            <div className="field" style={{ marginTop: 12 }}>
              <label htmlFor="responsibilities">Responsibilities / Duties</label>
              <textarea id="responsibilities" value={form.work.responsibilities} onChange={e => updateSection("work", "responsibilities", e.target.value)} />
            </div>
          </section>

          <section className="card">
            <div className="section-title">Section 5: Additional Information</div>

            {[
              { key: "employedBefore", text: "Have you ever been employed by this company in the past?" },
              { key: "authorizedToWork", text: "Are you a U.S. citizen, permanent resident, or a foreign national with authorization to work in the United States?" },
              { key: "driversLicense", text: "Do you have a driver's license?" },
              { key: "militaryService", text: "Have you ever served in the military?" },
              { key: "convictedFelony", text: "Have you ever been convicted of a felony?" }
            ].map(item => (
              <div key={item.key} style={{ marginBottom: 12 }}>
                <div className="radio-block">
                  <label>{item.text}</label>
                  <div className="radio-row">
                    <label><input type="radio" name={item.key} value="Yes" checked={form.additional[item.key] === "Yes"} onChange={e => updateSection("additional", item.key, e.target.value)} /> Yes</label>
                    <label><input type="radio" name={item.key} value="No" checked={form.additional[item.key] === "No"} onChange={e => updateSection("additional", item.key, e.target.value)} /> No</label>
                  </div>
                </div>

                {item.key === "convictedFelony" && form.additional.convictedFelony === "Yes" && (
                  <div className="field" style={{ marginTop: 10 }}>
                    <label htmlFor="felonyExplanation">If yes, please explain</label>
                    <textarea id="felonyExplanation" value={form.additional.felonyExplanation} onChange={e => updateSection("additional", "felonyExplanation", e.target.value)} />
                  </div>
                )}
              </div>
            ))}
          </section>

          <section className="card">
            <div className="section-title">Section 6: References</div>
            <div className="references-grid">
              {form.references.map((ref, index) => (
                <div className="reference-card" key={index}>
                  <h3>Reference {index + 1}</h3>
                  <div className="field">
                    <label htmlFor={`refName${index}`}>Name</label>
                    <input id={`refName${index}`} type="text" value={ref.name} onChange={e => updateReference(index, "name", e.target.value)} />
                  </div>
                  <div className="field" style={{ marginTop: 10*

