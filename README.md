<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ABE Admin: Edit Room | Best Day Ever Venues</title>
  <style>
    /* ── WB BRAND PALETTE ── */
    :root {
      --primary:   #596556;
      --primary-dk:#3d4d3a;
      --accent:    #a79277;
      --gold:      #c9bfb0;
      --text:      #3d3d3d;
      --text-lt:   #7a6e65;
      --border:    #e8e3dc;
      --white:     #FFFFFF;
      --cream:     #f9f7f4;
      --bg:        #f0ede8;
      --red:       #C0392B;
      --amber:     #D4810A;
      --amber-bg:  #fff8e6;
      --amber-bd:  #f5d28a;
      --new-bg:    #eaf3ea;
      --new-bd:    #596556;
      --font-head: Georgia, 'Times New Roman', serif;
      --font-body: 'Helvetica Neue', Helvetica, Arial, sans-serif;
      --font-mono: 'Courier New', Courier, monospace;
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: var(--font-body);
      font-size: 14px;
      background: #1a1a1a;
      color: var(--text);
    }

    /* ── DOCUMENT WRAPPER ── */
    .doc-wrapper { max-width: 1100px; margin: 0 auto; }

    /* ── DOCUMENT HEADER (outside the mockup) ── */
    .doc-header {
      background: var(--primary);
      padding: 32px 40px;
      border-bottom: 4px solid var(--accent);
    }
    .doc-header-inner { max-width: 1100px; margin: 0 auto; }
    .doc-tag { font-size: 10px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 8px; }
    .doc-header h1 { font-family: var(--font-head); font-size: 22px; font-weight: normal; color: var(--white); margin-bottom: 6px; }
    .doc-header p { font-size: 13px; color: rgba(255,255,255,0.65); max-width: 700px; }
    .doc-meta { display: flex; gap: 24px; flex-wrap: wrap; margin-top: 16px; }
    .doc-meta-item { font-size: 11px; color: rgba(255,255,255,0.55); }
    .doc-meta-item strong { color: var(--white); display: block; font-size: 12px; }

    /* ── CONTEXT NOTES STRIP ── */
    .context-strip {
      background: var(--amber-bg);
      border-top: 3px solid var(--amber);
      padding: 16px 32px;
    }
    .context-strip-inner { max-width: 1100px; margin: 0 auto; display: flex; gap: 24px; flex-wrap: wrap; }
    .context-point {
      display: flex; align-items: flex-start; gap: 8px; flex: 1; min-width: 260px;
    }
    .context-point-icon { font-size: 14px; flex-shrink: 0; margin-top: 1px; }
    .context-point-text { font-size: 12.5px; color: var(--text); line-height: 1.5; }
    .context-point-text strong { color: var(--amber); }

    /* ── BROWSER FRAME ── */
    .browser {
      background: #f0f0f0;
      border-top: 1px solid #333;
    }
    .browser-chrome {
      background: #EAECEF;
      padding: 10px 16px;
      display: flex; align-items: center; gap: 12px;
      border-bottom: 1px solid #C8CDD4;
    }
    .browser-dots { display: flex; gap: 6px; flex-shrink: 0; }
    .dot { width: 12px; height: 12px; border-radius: 50%; }
    .dot-r { background: #FF5F57; }
    .dot-y { background: #FEBC2E; }
    .dot-g { background: #28C840; }
    .browser-url { flex: 1; background: var(--white); border: 1px solid #C8CDD4; border-radius: 6px; padding: 5px 12px; font-size: 12px; color: var(--text-lt); max-width: 480px; }

    /* ── ADMIN SHELL ── */
    .admin-shell { display: flex; min-height: 860px; background: #f4f5f7; }

    /* ── ADMIN SIDEBAR ── */
    .admin-sidebar {
      width: 200px; flex-shrink: 0;
      background: var(--primary-dk);
      display: flex; flex-direction: column;
    }
    .sidebar-logo {
      padding: 16px 18px;
      border-bottom: 1px solid rgba(255,255,255,0.1);
      display: flex; align-items: center; gap: 10px;
    }
    .sidebar-logo-mark {
      width: 28px; height: 28px; background: rgba(255,255,255,0.18);
      border-radius: 5px; display: flex; align-items: center; justify-content: center;
      font-size: 10px; font-weight: 700; color: white; letter-spacing: 1px; flex-shrink: 0;
    }
    .sidebar-logo-name { font-size: 13px; font-weight: 700; color: var(--white); line-height: 1.2; }
    .sidebar-logo-sub { font-size: 9px; color: var(--gold); text-transform: uppercase; letter-spacing: 1px; }
    .sidebar-venue-picker {
      margin: 10px 12px;
      background: rgba(255,255,255,0.08); border: 1px solid rgba(255,255,255,0.12);
      border-radius: 6px; padding: 7px 10px;
      display: flex; align-items: center; justify-content: space-between;
    }
    .sidebar-venue-picker span { font-size: 11px; color: rgba(255,255,255,0.8); font-weight: 600; }
    .sidebar-venue-picker .chevron { font-size: 9px; color: rgba(255,255,255,0.4); }
    .sidebar-section { padding: 10px 0; border-bottom: 1px solid rgba(255,255,255,0.07); }
    .sidebar-section-label {
      font-size: 9px; font-weight: 700; letter-spacing: 1.5px; text-transform: uppercase;
      color: rgba(255,255,255,0.35); padding: 0 18px 6px;
    }
    .sidebar-link {
      display: flex; align-items: center; gap: 8px;
      padding: 8px 18px; font-size: 12.5px; color: rgba(255,255,255,0.65);
      cursor: pointer;
    }
    .sidebar-link:hover { background: rgba(255,255,255,0.06); }
    .sidebar-link.active { background: rgba(255,255,255,0.12); color: var(--white); }
    .sidebar-link.active .sidebar-icon { color: var(--gold); }
    .sidebar-icon { font-size: 13px; width: 16px; text-align: center; flex-shrink: 0; }
    .sidebar-badge {
      margin-left: auto; background: var(--accent); color: white;
      font-size: 9px; font-weight: 700; padding: 2px 6px; border-radius: 10px;
    }
    .sidebar-footer { margin-top: auto; padding: 14px 18px; border-top: 1px solid rgba(255,255,255,0.07); }
    .sidebar-user { font-size: 11px; color: rgba(255,255,255,0.5); }
    .sidebar-user strong { color: rgba(255,255,255,0.8); display: block; font-size: 12px; }

    /* ── ADMIN MAIN AREA ── */
    .admin-main { flex: 1; display: flex; flex-direction: column; min-width: 0; }

    /* ── PAGE HEADER ── */
    .admin-page-header {
      background: var(--white); border-bottom: 1px solid var(--border);
      padding: 14px 28px; display: flex; align-items: center; gap: 12px; flex-wrap: wrap;
    }
    .breadcrumb { font-size: 12px; color: var(--text-lt); display: flex; align-items: center; gap: 6px; }
    .breadcrumb a { color: var(--accent); text-decoration: none; }
    .breadcrumb-sep { color: var(--border); }
    .page-title { font-size: 18px; font-weight: 700; color: var(--text); margin-left: auto; flex-shrink: 0; }
    .page-actions { display: flex; gap: 8px; margin-left: 16px; }
    .btn-save {
      background: var(--primary); color: white; font-size: 12px; font-weight: 700;
      padding: 8px 20px; border-radius: 6px;
    }
    .btn-cancel {
      background: transparent; border: 1px solid var(--border); color: var(--text-lt);
      font-size: 12px; font-weight: 600; padding: 8px 16px; border-radius: 6px;
    }

    /* ── FORM AREA ── */
    .admin-form-area {
      flex: 1; padding: 24px 28px;
      display: grid; grid-template-columns: 1fr 280px; gap: 20px; align-items: start;
    }

    /* ── FORM CARD ── */
    .form-card {
      background: var(--white); border: 1px solid var(--border);
      border-radius: 10px; overflow: hidden; margin-bottom: 16px;
    }
    .form-card:last-child { margin-bottom: 0; }
    .form-card-head {
      background: var(--cream); border-bottom: 1px solid var(--border);
      padding: 12px 20px; display: flex; align-items: center; gap: 10px;
    }
    .form-card-title { font-size: 13px; font-weight: 700; color: var(--text); }
    .form-card-subtitle { font-size: 11px; color: var(--text-lt); margin-left: auto; }
    .form-card-body { padding: 18px 20px; }

    /* ── NEW SECTION HIGHLIGHTING ── */
    .form-card.new-section { border: 2px solid var(--primary); }
    .form-card.new-section .form-card-head {
      background: var(--new-bg); border-bottom: 2px solid var(--primary);
    }
    .new-badge {
      background: var(--primary); color: white; font-size: 9px; font-weight: 700;
      padding: 2px 8px; border-radius: 10px; text-transform: uppercase; letter-spacing: 0.5px;
    }

    /* ── MERGE TAG CALLOUT ── */
    .merge-callout {
      background: var(--amber-bg); border: 1px solid var(--amber-bd);
      border-left: 3px solid var(--amber); border-radius: 0 6px 6px 0;
      padding: 10px 14px; margin-top: 10px; font-size: 12px; color: var(--text);
      line-height: 1.5;
    }
    .merge-callout strong { color: var(--amber); display: block; font-size: 11px; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px; }
    .merge-tag { font-family: var(--font-mono); font-size: 11px; background: var(--white); border: 1px solid var(--amber-bd); border-radius: 3px; padding: 1px 5px; color: var(--amber); }
    .sirvoy-note {
      background: #fde8e6; border: 1px solid #f2c0bc;
      border-left: 3px solid var(--red); border-radius: 0 6px 6px 0;
      padding: 8px 14px; margin-top: 8px; font-size: 11.5px; color: var(--text); line-height: 1.5;
    }
    .sirvoy-note strong { color: var(--red); font-size: 10px; text-transform: uppercase; letter-spacing: 0.5px; display: block; margin-bottom: 3px; }

    /* ── FORM ELEMENTS ── */
    .form-row { margin-bottom: 16px; }
    .form-row:last-child { margin-bottom: 0; }
    .form-row-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 16px; }
    .form-row-2:last-child { margin-bottom: 0; }
    .form-label {
      font-size: 12px; font-weight: 700; color: var(--text);
      margin-bottom: 5px; display: flex; align-items: center; gap: 6px;
    }
    .form-label-req { color: var(--accent); }
    .form-label-hint { font-weight: 400; color: var(--text-lt); font-size: 11px; }
    .form-input {
      width: 100%; border: 1px solid var(--border); border-radius: 6px;
      padding: 9px 12px; font-size: 13px; color: var(--text); background: var(--white);
      font-family: var(--font-body);
    }
    .form-input:focus { border-color: var(--accent); outline: none; }
    .form-input.new-field { border-color: var(--primary); background: var(--new-bg); }
    .form-textarea {
      width: 100%; border: 1px solid var(--border); border-radius: 6px;
      padding: 9px 12px; font-size: 13px; color: var(--text); background: var(--white);
      font-family: var(--font-body); resize: vertical; min-height: 100px;
    }
    .form-select {
      width: 100%; border: 1px solid var(--border); border-radius: 6px;
      padding: 9px 12px; font-size: 13px; color: var(--text); background: var(--white);
      appearance: none; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%237a6e65' fill='none' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E");
      background-repeat: no-repeat; background-position: right 12px center;
      padding-right: 32px;
    }
    .form-select.new-field { border-color: var(--primary); background-color: var(--new-bg); }
    .form-hint { font-size: 11px; color: var(--text-lt); margin-top: 4px; }

    /* ── IMAGE UPLOAD ── */
    .img-upload-area {
      border: 2px dashed var(--border); border-radius: 8px;
      padding: 20px; text-align: center; background: var(--cream); margin-bottom: 12px;
    }
    .img-upload-area p { font-size: 12px; color: var(--text-lt); margin: 4px 0; }
    .btn-upload {
      background: transparent; border: 1px solid var(--accent); color: var(--accent);
      font-size: 12px; font-weight: 600; padding: 7px 16px; border-radius: 6px;
      display: inline-block; margin-top: 8px;
    }
    .img-thumb-row { display: flex; gap: 10px; flex-wrap: wrap; }
    .img-thumb {
      width: 80px; height: 60px; background: var(--bg);
      border: 1px solid var(--border); border-radius: 6px;
      overflow: hidden; display: flex; align-items: center; justify-content: center;
      font-size: 9px; color: var(--text-lt); position: relative; flex-shrink: 0;
    }
    .img-thumb-del {
      position: absolute; top: 3px; right: 3px; width: 16px; height: 16px;
      background: var(--red); border-radius: 50%; color: white;
      font-size: 8px; font-weight: 700; display: flex; align-items: center; justify-content: center;
    }
    .img-thumb img { width: 100%; height: 100%; object-fit: cover; }
    .img-caption { font-size: 10px; color: var(--text-lt); margin-top: 8px; }

    /* ── AMENITIES ── */
    .amenities-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; }
    .amenity-row { display: flex; align-items: center; gap: 8px; padding: 4px 0; }
    .amenity-check {
      width: 16px; height: 16px; border-radius: 3px; border: 1.5px solid var(--border);
      flex-shrink: 0; display: flex; align-items: center; justify-content: center;
    }
    .amenity-check.checked { background: var(--primary); border-color: var(--primary); }
    .amenity-check.checked::after { content: 'v'; font-size: 8px; color: white; font-weight: 900; }
    .amenity-label { font-size: 12px; color: var(--text); }

    /* ── SETTINGS PANEL ── */
    .settings-stack { display: flex; flex-direction: column; gap: 16px; }
    .settings-card {
      background: var(--white); border: 1px solid var(--border);
      border-radius: 10px; overflow: hidden;
    }
    .settings-card-head {
      background: var(--cream); border-bottom: 1px solid var(--border);
      padding: 10px 16px;
    }
    .settings-card-title { font-size: 12px; font-weight: 700; color: var(--text); }
    .settings-card-body { padding: 14px 16px; }

    .toggle-row { display: flex; align-items: center; justify-content: space-between; padding: 6px 0; }
    .toggle-label { font-size: 12.5px; color: var(--text); }
    .toggle-switch {
      width: 36px; height: 20px; background: var(--border);
      border-radius: 10px; position: relative; flex-shrink: 0;
    }
    .toggle-switch.on { background: var(--primary); }
    .toggle-knob {
      width: 14px; height: 14px; background: white; border-radius: 50%;
      position: absolute; top: 3px; left: 3px;
      box-shadow: 0 1px 3px rgba(0,0,0,0.2);
    }
    .toggle-switch.on .toggle-knob { left: 19px; }

    .sort-input {
      width: 100%; border: 1px solid var(--border); border-radius: 6px;
      padding: 7px 10px; font-size: 13px; color: var(--text); background: var(--white);
    }

    /* ── MERGE TAG REGISTER NOTICE ── */
    .register-notice {
      background: var(--amber-bg); border: 1px solid var(--amber-bd);
      border-radius: 10px; padding: 16px 20px; margin-bottom: 20px;
    }
    .register-notice h3 { font-size: 12px; font-weight: 700; color: var(--amber); text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 8px; }
    .register-notice p { font-size: 12.5px; color: var(--text); line-height: 1.6; margin-bottom: 6px; }
    .register-notice p:last-child { margin-bottom: 0; }
    .tag-inline { font-family: var(--font-mono); font-size: 11px; background: rgba(212,129,10,0.1); border: 1px solid var(--amber-bd); border-radius: 3px; padding: 1px 5px; color: var(--amber); }

    /* ── FOOTER ── */
    .doc-footer {
      background: var(--primary); color: rgba(255,255,255,0.55);
      text-align: center; padding: 18px 24px; font-size: 11px;
    }
    .doc-footer strong { color: var(--white); }

    /* ── COMPARISON TABLE ── */
    .comparison-section { background: var(--white); padding: 28px 32px; border-top: 1px solid var(--border); }
    .comparison-section-inner { max-width: 1060px; margin: 0 auto; }
    .comparison-section h2 { font-family: var(--font-head); font-size: 18px; font-weight: normal; color: var(--text); margin-bottom: 16px; border-bottom: 2px solid var(--accent); padding-bottom: 8px; }
    table.comp-table { width: 100%; border-collapse: collapse; font-size: 12.5px; }
    .comp-table thead { background: var(--text); }
    .comp-table thead th { padding: 10px 14px; text-align: left; color: white; font-size: 11px; font-weight: 700; letter-spacing: 0.5px; }
    .comp-table tbody tr { border-bottom: 1px solid var(--border); }
    .comp-table tbody tr:last-child { border-bottom: none; }
    .comp-table td { padding: 10px 14px; vertical-align: top; color: var(--text-lt); }
    .comp-table td:first-child { color: var(--text); font-weight: 600; }
    .status-new { background: var(--new-bg); color: var(--primary); font-size: 10px; font-weight: 700; padding: 2px 7px; border-radius: 10px; white-space: nowrap; }
    .status-changed { background: var(--amber-bg); color: var(--amber); font-size: 10px; font-weight: 700; padding: 2px 7px; border-radius: 10px; white-space: nowrap; }
    .status-same { background: var(--bg); color: var(--text-lt); font-size: 10px; font-weight: 700; padding: 2px 7px; border-radius: 10px; white-space: nowrap; }
    .tag-cell { font-family: var(--font-mono); font-size: 10.5px; color: var(--primary); }
  </style>
</head>
<body>

<!-- ══════════════════════════════════════════════
     DOCUMENT HEADER
══════════════════════════════════════════════ -->
<div class="doc-header">
  <div class="doc-header-inner">
    <div class="doc-tag">Best Day Ever Venues / Internal / ABE Admin</div>
    <h1>ABE: Admin Panel Mockup / Edit Room</h1>
    <p>Shows the per-room configuration screen in the ABE admin panel, including the new dedicated check-in time and check-out time fields. This resolves Open Question 3 from ABE_Context ("Where is check-in time held?") as a per-room setting, and introduces a new merge tag for check-out time.</p>
    <div class="doc-meta">
      <div class="doc-meta-item"><strong>Sirvoy comparison</strong>Screenshot provided April 2026</div>
      <div class="doc-meta-item"><strong>New fields</strong>Check-in time, Check-out time, Room strapline</div>
      <div class="doc-meta-item"><strong>Resolves</strong>ABE_Context Open Question 3</div>
      <div class="doc-meta-item"><strong>New merge tag</strong>*|ABE_CHECKOUT_TIME|*</div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════
     CONTEXT NOTES
══════════════════════════════════════════════ -->
<div class="context-strip">
  <div class="context-strip-inner">
    <div class="context-point">
      <div class="context-point-icon">&#128275;</div>
      <div class="context-point-text"><strong>Sirvoy workaround removed:</strong> In Sirvoy, check-in time is embedded in the room name ("3 Double - 2pm Check-in") and in the description text. ABE gives each room a dedicated time field, so the room name stays clean.</div>
    </div>
    <div class="context-point">
      <div class="context-point-icon">&#128338;</div>
      <div class="context-point-text"><strong>Two new merge tags:</strong> <code>*|ABE_CHECKIN_TIME|*</code> (already in register, source now confirmed as per-room) and <code>*|ABE_CHECKOUT_TIME|*</code> (NEW, not yet in register). Both need adding to the ABE_Mailchimp_Merge_Tag_Register.</div>
    </div>
    <div class="context-point">
      <div class="context-point-icon">&#128247;</div>
      <div class="context-point-text"><strong>One additional improvement:</strong> A short "strapline" field has been added (one line, shown on the guest-facing room card). Previously, Sirvoy's single description field mixed the card-level summary with the full detail text.</div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════
     BROWSER FRAME + ADMIN MOCKUP
══════════════════════════════════════════════ -->
<div class="doc-wrapper">
<div class="browser">
  <div class="browser-chrome">
    <div class="browser-dots"><span class="dot dot-r"></span><span class="dot dot-y"></span><span class="dot dot-g"></span></div>
    <div class="browser-url">abe.bestdayever-venues.co.uk/admin/rooms/edit/WB-SC-03</div>
  </div>

  <div class="admin-shell">

    <!-- ── SIDEBAR ── -->
    <div class="admin-sidebar">
      <div class="sidebar-logo">
        <div class="sidebar-logo-mark">ABE</div>
        <div>
          <div class="sidebar-logo-name">ABE Admin</div>
          <div class="sidebar-logo-sub">Best Day Ever Venues</div>
        </div>
      </div>

      <div class="sidebar-venue-picker">
        <span>Whistle Barns</span>
        <span class="chevron">&#9660;</span>
      </div>

      <div class="sidebar-section">
        <div class="sidebar-section-label">Bookings</div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128197;</span> Dashboard
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128221;</span> All bookings
          <span class="sidebar-badge">7</span>
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128100;</span> Guests
        </div>
      </div>

      <div class="sidebar-section">
        <div class="sidebar-section-label">Configuration</div>
        <div class="sidebar-link active">
          <span class="sidebar-icon">&#127968;</span> Rooms
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#11088;</span> Extras
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128178;</span> Pricing
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128197;</span> Availability
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128274;</span> Invitation codes
        </div>
      </div>

      <div class="sidebar-section">
        <div class="sidebar-section-label">System</div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#128202;</span> Reports
        </div>
        <div class="sidebar-link">
          <span class="sidebar-icon">&#9881;</span> Venue settings
        </div>
      </div>

      <div class="sidebar-footer">
        <div class="sidebar-user">
          <strong>MARIALARCOMBE</strong>
          Administrator
        </div>
      </div>
    </div>

    <!-- ── MAIN AREA ── -->
    <div class="admin-main">

      <!-- Page header -->
      <div class="admin-page-header">
        <div class="breadcrumb">
          <a href="#">Rooms</a>
          <span class="breadcrumb-sep">›</span>
          <span>Edit room</span>
        </div>
        <div class="page-title">Edit room</div>
        <div class="page-actions">
          <div class="btn-cancel">Cancel</div>
          <div class="btn-save">Save room</div>
        </div>
      </div>

      <!-- Form area -->
      <div class="admin-form-area">

        <!-- LEFT: main form -->
        <div>

          <!-- Room identity -->
          <div class="form-card">
            <div class="form-card-head">
              <div class="form-card-title">Room identity</div>
            </div>
            <div class="form-card-body">
              <div class="form-row">
                <label class="form-label">Room name <span class="form-label-req">*</span></label>
                <input class="form-input" type="text" value="Shipping Container: 3 Double" />
                <div class="form-hint">Use a clear, descriptive name. Do not include check-in time in the name; that is set below.</div>
                <div class="sirvoy-note">
                  <strong>Change from Sirvoy</strong>
                  In Sirvoy this room was named "3 Double - 2pm Check-in - Shipping Container" to surface the check-in time to guests. In ABE the time has its own field (see Arrival and Departure below), so the name stays clean.
                </div>
              </div>
              <div class="form-row-2">
                <div>
                  <label class="form-label">Room reference <span class="form-label-hint">(internal)</span></label>
                  <input class="form-input" type="text" value="WB-SC-03" />
                  <div class="form-hint">Short code used in ABE reports and booking references.</div>
                </div>
                <div>
                  <label class="form-label">Room type / class</label>
                  <select class="form-select">
                    <option>Room</option>
                    <option>Suite</option>
                    <option>Family room</option>
                  </select>
                </div>
              </div>
            </div>
          </div>

          <!-- ARRIVAL AND DEPARTURE TIMES: NEW SECTION -->
          <div class="form-card new-section">
            <div class="form-card-head">
              <div class="form-card-title">Arrival and departure times</div>
              <span class="new-badge">New in ABE</span>
              <div class="form-card-subtitle">Per-room configuration</div>
            </div>
            <div class="form-card-body">

              <div class="form-row-2">
                <div>
                  <label class="form-label">Check-in time <span class="form-label-req">*</span></label>
                  <select class="form-select new-field">
                    <option>12:00 noon</option>
                    <option>1:00 pm</option>
                    <option selected>2:00 pm</option>
                    <option>3:00 pm</option>
                  </select>
                  <div class="form-hint">Shown to guests on the booking confirmation, room card, and all pre-stay reminder emails.</div>
                  <div class="merge-callout">
                    <strong>Feeds Mailchimp merge tag</strong>
                    <span class="merge-tag">*|ABE_CHECKIN_TIME|*</span>: used in WB-ABE-01 (Booking Confirmation), WB-ABE-03 (Info Pack), WB-ABE-04 (7-Day Reminder), WB-ABE-05 (Day Before). This resolves the source of this tag as per-room config.
                  </div>
                </div>
                <div>
                  <label class="form-label">Check-out time <span class="form-label-req">*</span></label>
                  <select class="form-select new-field">
                    <option>10:00 am</option>
                    <option selected>10:30 am</option>
                    <option>11:00 am</option>
                    <option>12:00 noon</option>
                  </select>
                  <div class="form-hint">Standard at Whistle Barns is 10:30 am. Set per room to allow for late check-out room types.</div>
                  <div class="merge-callout">
                    <strong>New merge tag required</strong>
                    <span class="merge-tag">*|ABE_CHECKOUT_TIME|*</span>: this tag does not yet exist in the merge tag register. Pete to add. Required for room cards (Screen 2) and the review/confirmation screens. Check-out time currently appears in Sirvoy descriptions only; there is no tag for it.
                  </div>
                </div>
              </div>

            </div>
          </div>

          <!-- Description -->
          <div class="form-card">
            <div class="form-card-head">
              <div class="form-card-title">Description and content</div>
            </div>
            <div class="form-card-body">
              <div class="form-row">
                <label class="form-label">
                  Room strapline
                  <span class="new-badge" style="font-size:8px; padding:1px 6px;">New in ABE</span>
                </label>
                <input class="form-input new-field" type="text" value="Air-conditioned shipping container with en-suite shower, sleeps 2" />
                <div class="form-hint">One line. Shown under the room name on the guest booking card. No check-in time needed here; that appears as a tag.</div>
                <div class="merge-callout">
                  <strong>Why this field exists</strong>
                  In Sirvoy there is a single description field used for both the card-level summary and the "Read more" detail. ABE separates these so the short summary on the booking card stays concise and the full detail is available on expansion.
                </div>
              </div>
              <div class="form-row" style="margin-top:16px;">
                <label class="form-label">Full description</label>
                <textarea class="form-textarea" style="min-height:120px;">Enjoy a truly unique overnight stay in our incredible, up-cycled shipping containers. Fully air-conditioned double bedroom, sleeping 2 adults, with en-suite shower room.

Bedrooms include tea and coffee making facilities, a mini fridge, luxury toiletries, hairdryer, bottled water, bed linen and towels. Price includes a Grab and Go Continental Breakfast Bag.</textarea>
                <div class="form-hint">Shown in the "Read more" section on the booking page. Do not include check-in or check-out times; these are displayed automatically from the fields above. Do not mention travel cots here; configure those in Extras.</div>
              </div>
            </div>
          </div>

          <!-- Images -->
          <div class="form-card">
            <div class="form-card-head">
              <div class="form-card-title">Room photos</div>
              <div class="form-card-subtitle">Drag to reorder. First image is the card cover.</div>
            </div>
            <div class="form-card-body">
              <div class="img-thumb-row" style="margin-bottom:12px;">
                <div class="img-thumb">
                  <div style="font-size:9px; color:var(--text-lt); text-align:center; padding:4px;">Shipping-containers&#8203;-at-Whistle-Barns.jpg</div>
                  <div class="img-thumb-del">x</div>
                </div>
                <div class="img-upload-area" style="flex:1; padding:12px; margin-bottom:0;">
                  <p>Drop images here or</p>
                  <div class="btn-upload">Choose files</div>
                  <p style="margin-top:6px; font-size:10px;">JPG or PNG. Min 1200px wide. Max 5 images.</p>
                </div>
              </div>
              <div class="img-caption">Tap any image to set alt text (required for accessibility).</div>
            </div>
          </div>

          <!-- Pricing -->
          <div class="form-card">
            <div class="form-card-head">
              <div class="form-card-title">Capacity and pricing</div>
            </div>
            <div class="form-card-body">
              <div class="form-row-2">
                <div>
                  <label class="form-label">Maximum occupancy <span class="form-label-req">*</span></label>
                  <select class="form-select">
                    <option>1</option>
                    <option selected>2</option>
                    <option>3</option>
                    <option>4</option>
                    <option>5</option>
                    <option>6</option>
                  </select>
                  <div class="form-hint">The guest count stepper on the booking page will allow up to this number. Do not cap family rooms at 2.</div>
                </div>
                <div>
                  <label class="form-label">Price model</label>
                  <select class="form-select">
                    <option selected>Fixed (per night)</option>
                    <option>Variable (by date)</option>
                  </select>
                </div>
              </div>
              <div class="form-row-2" style="margin-top:14px;">
                <div>
                  <label class="form-label">Nightly rate <span class="form-label-req">*</span></label>
                  <input class="form-input" type="text" value="125.00" />
                  <div class="form-hint">Enter net price excluding VAT. Format: 000.00</div>
                </div>
                <div>
                  <label class="form-label">VAT rate</label>
                  <select class="form-select">
                    <option selected>20.00% (Standard)</option>
                    <option>5.00% (Reduced)</option>
                    <option>0.00% (Zero)</option>
                  </select>
                </div>
              </div>
            </div>
          </div>

        </div><!-- end left column -->

        <!-- RIGHT: settings panel -->
        <div class="settings-stack">

          <!-- Status -->
          <div class="settings-card">
            <div class="settings-card-head"><div class="settings-card-title">Status</div></div>
            <div class="settings-card-body">
              <div class="toggle-row">
                <span class="toggle-label">Active (visible to guests)</span>
                <div class="toggle-switch on"><div class="toggle-knob"></div></div>
              </div>
              <div class="toggle-row">
                <span class="toggle-label">Internal room (staff only)</span>
                <div class="toggle-switch"><div class="toggle-knob"></div></div>
              </div>
            </div>
          </div>

          <!-- Sort order -->
          <div class="settings-card">
            <div class="settings-card-head"><div class="settings-card-title">Display order</div></div>
            <div class="settings-card-body">
              <label class="form-label" style="margin-bottom:6px;">Sort position</label>
              <input class="sort-input" type="number" value="5" min="1" />
              <div class="form-hint" style="margin-top:5px;">Lower numbers appear first on the booking page.</div>
            </div>
          </div>

          <!-- Amenities -->
          <div class="settings-card">
            <div class="settings-card-head"><div class="settings-card-title">Amenities</div></div>
            <div class="settings-card-body">
              <div class="amenities-grid">
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">WiFi</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">TV</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check checked"></div>
                  <span class="amenity-label">Air conditioning</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Fan</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check checked"></div>
                  <span class="amenity-label">Shower</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Bath</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Refrigerator</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Microwave</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check checked"></div>
                  <span class="amenity-label">Coffee machine</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Washing machine</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Accessible</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Pet friendly</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check checked"></div>
                  <span class="amenity-label">Non-smoking</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Gym</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Pool</span>
                </div>
                <div class="amenity-row">
                  <div class="amenity-check"></div>
                  <span class="amenity-label">Wake-up service</span>
                </div>
              </div>
              <div class="form-hint" style="margin-top:10px;">Ticked amenities appear as tags on the guest-facing room card.</div>
            </div>
          </div>

          <!-- Categories -->
          <div class="settings-card">
            <div class="settings-card-head"><div class="settings-card-title">Categories</div></div>
            <div class="settings-card-body">
              <div class="amenity-row" style="margin-bottom:6px;">
                <div class="amenity-check checked"></div>
                <span class="amenity-label">Guest accommodation</span>
              </div>
              <div class="amenity-row">
                <div class="amenity-check"></div>
                <span class="amenity-label">Accessible room</span>
              </div>
            </div>
          </div>

        </div><!-- end settings panel -->

      </div><!-- end form area -->
    </div><!-- end admin main -->
  </div><!-- end admin shell -->
</div><!-- end browser -->
</div><!-- end doc wrapper -->


<!-- ══════════════════════════════════════════════
     FIELD COMPARISON TABLE
══════════════════════════════════════════════ -->
<div class="comparison-section">
  <div class="comparison-section-inner">
    <h2>Field-by-field comparison: Sirvoy vs. ABE</h2>
    <table class="comp-table">
      <thead>
        <tr>
          <th>Field</th>
          <th>Sirvoy</th>
          <th>ABE</th>
          <th>Status</th>
          <th>Merge tag</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Room name</td>
          <td>Free text: currently includes check-in time (e.g. "3 Double - 2pm Check-in")</td>
          <td>Free text: clean name only. Time is a separate field.</td>
          <td><span class="status-changed">Changed</span></td>
          <td class="tag-cell">*|ABE_ROOM_NAME|*</td>
        </tr>
        <tr>
          <td>Room strapline</td>
          <td>Not available. Key details mixed into the description.</td>
          <td>New short field (one line). Shown on the guest-facing room card.</td>
          <td><span class="status-new">New in ABE</span></td>
          <td class="tag-cell">None (display only)</td>
        </tr>
        <tr>
          <td>Check-in time</td>
          <td>Embedded in room name and/or description text. No dedicated field.</td>
          <td>Dedicated dropdown, per room. Options: 12:00 noon, 1:00 pm, 2:00 pm, 3:00 pm.</td>
          <td><span class="status-new">New in ABE</span></td>
          <td class="tag-cell">*|ABE_CHECKIN_TIME|*</td>
        </tr>
        <tr>
          <td>Check-out time</td>
          <td>In description text only ("Check Out 10.30am"). No dedicated field.</td>
          <td>Dedicated dropdown, per room. Options: 10:00 am, 10:30 am, 11:00 am, 12:00 noon.</td>
          <td><span class="status-new">New in ABE</span></td>
          <td class="tag-cell">*|ABE_CHECKOUT_TIME|* (new tag, not yet in register)</td>
        </tr>
        <tr>
          <td>Full description</td>
          <td>Single textarea. Contains check-in/out times, breakfast info, and travel cot note.</td>
          <td>Textarea for room description only. Times come from dedicated fields. Travel cot handled in Extras.</td>
          <td><span class="status-changed">Changed</span></td>
          <td class="tag-cell">None (display only)</td>
        </tr>
        <tr>
          <td>Room photos</td>
          <td>Single image upload. 408KB shown.</td>
          <td>Multi-image upload (up to 5). First image is card cover. Alt text required.</td>
          <td><span class="status-changed">Changed</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Maximum occupancy</td>
          <td>"Number of guests" (default) and "Max. guests": both set to 2 in the Sirvoy screenshot.</td>
          <td>Single "Maximum occupancy" dropdown. Guest count stepper on booking page goes from 1 to this value.</td>
          <td><span class="status-changed">Simplified</span></td>
          <td class="tag-cell">Used to cap *|ABE_GUESTS|* stepper</td>
        </tr>
        <tr>
          <td>Price model</td>
          <td>Fixed / Variable dropdown.</td>
          <td>Fixed (per night) / Variable (by date). Same concept.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Nightly rate</td>
          <td>Price field (£125.00 in screenshot).</td>
          <td>Nightly rate field. Net price excluding VAT.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">*|ABE_ROOM_PRICE|*</td>
        </tr>
        <tr>
          <td>VAT rate</td>
          <td>VAT rate dropdown (20% in screenshot).</td>
          <td>VAT rate dropdown (Standard 20%, Reduced 5%, Zero 0%).</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Room type / class</td>
          <td>"Class" dropdown (Room selected).</td>
          <td>"Room type / class" dropdown (Room, Suite, Family room).</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Amenities</td>
          <td>Checkbox grid (15 options). Same selection.</td>
          <td>Checkbox grid (16 options, same as Sirvoy). Ticked items appear as tags on the guest room card.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Sort order</td>
          <td>"Sort order" numeric field (5 in screenshot).</td>
          <td>"Display order" numeric field. Same function.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Internal room toggle</td>
          <td>"Internal room type" toggle (off in screenshot).</td>
          <td>"Internal room (staff only)" toggle. Same function.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Categories</td>
          <td>"Guest Accommodation" checkbox (ticked).</td>
          <td>"Guest accommodation" checkbox plus "Accessible room" as a separate category option.</td>
          <td><span class="status-same">Same</span></td>
          <td class="tag-cell">None</td>
        </tr>
        <tr>
          <td>Room reference</td>
          <td>Not available.</td>
          <td>Short internal code (e.g. WB-SC-03). Used in ABE reports and booking references.</td>
          <td><span class="status-new">New in ABE</span></td>
          <td class="tag-cell">Part of *|ABE_BOOKING_REF|*</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<div class="doc-footer">
  <strong>ABE Admin: Edit Room Mockup</strong> &bull; Best Day Ever Venues &bull; Internal document &bull; April 2026<br>
  For Pete Sheldrake (developer) &bull; maria@ensarb.com
</div>

</body>
</html>
