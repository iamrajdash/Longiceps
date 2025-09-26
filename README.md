<!doctype html>
<html lang="en" ng-app="LongicepsApp">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Longiceps — RedHat-based IT Training (Linux, Ansible, OpenShift)</title>
  <meta name="description" content="Longiceps — Global RedHat curriculum training for IT professionals: Linux (RHCSA/RHCE), Ansible automation, and OpenShift." />
  <link rel="icon" href="data:;base64,iVBORw0KGgo=" />

  <!-- Google Fonts (optional) -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg: #0f172a;
      --card: #0b1220;
      --accent: #4f46e5;
      --muted: #94a3b8;
      --glass: rgba(255,255,255,0.03);
      --max-width: 1100px;
      --radius: 12px;
      color-scheme: dark;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,Arial;color:#e6eef8;background:linear-gradient(180deg,#071029 0%, #081226 60%);}
    a{color:var(--accent);text-decoration:none}
    header{backdrop-filter: blur(6px);position:sticky;top:0;z-index:40;background:linear-gradient(180deg, rgba(6,10,24,0.6), rgba(6,10,24,0.4));box-shadow:0 1px 0 rgba(255,255,255,0.02)}
    .container{max-width:var(--max-width);margin:0 auto;padding:1rem}

    /* Navbar */
    .nav{display:flex;align-items:center;justify-content:space-between;padding:0.5rem 0}
    .brand{display:flex;align-items:center;gap:0.75rem}
    .logo{width:44px;height:44px;background:linear-gradient(135deg,#7c3aed,#06b6d4);border-radius:10px;display:flex;align-items:center;justify-content:center;font-weight:700;color:white}
    .nav-links{display:flex;gap:1rem;align-items:center}
    .nav-links a{padding:0.45rem 0.6rem;border-radius:8px;color:#cfe6ff;font-weight:500}
    .nav-links a:hover{background:var(--glass)}
    .cta{background:var(--accent);padding:0.5rem 0.8rem;border-radius:10px;color:white;font-weight:600}

    /* Hero */
    .hero{padding:3.2rem 0;display:grid;grid-template-columns:1fr 420px;gap:2rem;align-items:center}
    .hero .eyebrow{color:var(--muted);font-size:0.9rem}
    .hero h1{font-size:2.05rem;margin:0 0 0.6rem}
    .hero p{color:var(--muted);margin:0 0 1rem}
    .hero .actions{display:flex;gap:0.75rem}

    /* Card */
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:1rem;border-radius:var(--radius);box-shadow:0 8px 30px rgba(2,6,23,0.6);}

    /* Courses grid */
    .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-top:1rem}
    .course{padding:1rem;border-radius:10px;background:rgba(255,255,255,0.02)}
    .course h3{margin:0 0 0.5rem}
    .course p{margin:0;color:var(--muted)}

    /* Sections */
    section{padding:2.4rem 0}
    h2.section-title{margin:0 0 1rem}

    /* Contact */
    form .row{display:flex;gap:0.75rem}
    input,textarea,select{width:100%;padding:0.65rem;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit}
    textarea{min-height:110px;resize:vertical}
    .btn{display:inline-block;padding:0.6rem 0.9rem;border-radius:8px;background:var(--accent);color:white;font-weight:600}

    footer{padding:2rem 0;border-top:1px solid rgba(255,255,255,0.02);color:var(--muted)}

    /* Responsive */
    @media (max-width:900px){
      .hero{grid-template-columns:1fr;}
      .grid{grid-template-columns:repeat(1,1fr)}
      .nav-links{display:none}
      .mobile-nav{display:flex}
    }

    /* small styles */
    .muted{color:var(--muted)}
    .pill{display:inline-block;padding:0.25rem 0.6rem;border-radius:999px;background:rgba(255,255,255,0.03);font-weight:600}

    /* Simple footer grid */
    .footer-grid{display:flex;gap:2rem;flex-wrap:wrap}
    .footer-grid .col{min-width:180px}

    /* Smooth anchor scrolling */
    html{scroll-behavior:smooth}

  </style>

  <!-- AngularJS v1.x -->
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.3/angular.min.js"></script>

</head>
<body ng-controller="MainCtrl as vm">
  <header>
    <div class="container nav">
      <div class="brand">
        <div class="logo">L</div>
        <div>
          <div style="font-weight:700">Longiceps</div>
          <div style="font-size:12px;color:var(--muted);margin-top:2px">RedHat curriculum — Linux • Ansible • OpenShift</div>
        </div>
      </div>

      <nav>
        <div class="nav-links">
          <a href="#home">Home</a>
          <a href="#courses">Courses</a>
          <a href="#certificates">Certifications</a>
          <a href="#about">About</a>
          <a href="#contact" class="cta">Enroll Now</a>
        </div>
      </nav>

      <div class="mobile-nav">
        <button ng-click="vm.openNav = !vm.openNav" aria-label="menu" style="background:none;border:0;color:var(--muted)">☰</button>
      </div>
    </div>

    <div ng-show="vm.openNav" style="padding:0 1rem 1rem;background:linear-gradient(180deg, rgba(6,10,24,0.9), rgba(6,10,24,0.85))">
      <div class="container card">
        <a href="#home" ng-click="vm.openNav=false">Home</a><br>
        <a href="#courses" ng-click="vm.openNav=false">Courses</a><br>
        <a href="#certificates" ng-click="vm.openNav=false">Certifications</a><br>
        <a href="#about" ng-click="vm.openNav=false">About</a><br>
        <a href="#contact" class="cta" ng-click="vm.openNav=false">Enroll Now</a>
      </div>
    </div>
  </header>

  <main class="container">

    <!-- HERO -->
    <section id="home" class="hero">
      <div>
        <div class="eyebrow">Instructor-led · Global · RedHat aligned</div>
        <h1>Master RedHat technologies — Linux, Ansible & OpenShift</h1>
        <p>Longiceps provides hands-on, certification-aligned training for IT professionals and system administrators. Our courses map directly to RedHat certifications (RHCSA, RHCE, Ansible Automation, OpenShift Administrator) and focus on practical skills employers want.</p>

        <div class="actions">
          <a href="#courses" class="btn">Explore Courses</a>
          <a href="#contact" class="pill">Request Syllabus</a>
        </div>

        <div style="margin-top:1rem;color:var(--muted)">
          <strong>Format:</strong> Live online cohorts · On-demand labs · Corporate training
        </div>

        <div style="margin-top:1.2rem;display:flex;gap:1rem;align-items:center">
          <div class="card" style="padding:0.7rem;display:flex;gap:0.7rem;align-items:center;">
            <div style="font-weight:700;font-size:1.1rem">98%</div>
            <div class="muted">Learner satisfaction (sample cohort)</div>
          </div>
          <div class="card" style="padding:0.7rem;display:flex;gap:0.7rem;align-items:center;">
            <div style="font-weight:700;font-size:1.1rem">Global</div>
            <div class="muted">Learners across timezones</div>
          </div>
        </div>
      </div>

      <aside class="card">
        <h3 style="margin-top:0">Upcoming Cohorts</h3>
        <div ng-repeat="cohort in vm.cohorts">
          <strong>{{cohort.title}}</strong>
          <div class="muted" style="font-size:13px">Starts: {{cohort.start | date:'mediumDate'}}</div>
          <div style="margin-top:6px">{{cohort.desc}}</div>
          <div style="margin-top:8px"><a href="#contact" class="pill">Enroll</a></div>
          <hr style="border:none;border-top:1px solid rgba(255,255,255,0.03);margin:12px 0">
        </div>
      </aside>
    </section>

    <!-- COURSES -->
    <section id="courses">
      <h2 class="section-title">Courses</h2>
      <p class="muted">Focused, practical courses aligned to RedHat certifications and enterprise needs.</p>

      <div class="grid" aria-live="polite">
        <article class="course card" ng-repeat="course in vm.courses">
          <div style="display:flex;justify-content:space-between;align-items:start">
            <div>
              <h3>{{course.title}}</h3>
              <div class="muted" style="font-size:13px">Level: {{course.level}} · Duration: {{course.duration}}</div>
            </div>
            <div style="text-align:right">
              <div style="font-weight:700">{{course.mode}}</div>
              <div style="font-size:13px;color:var(--muted)">Seats: {{course.seats}}</div>
            </div>
          </div>
          <p class="muted" style="margin-top:0.6rem">{{course.description}}</p>
          <div style="margin-top:0.8rem;display:flex;gap:0.5rem">
            <a href="#contact" class="btn">Enroll</a>
            <a href="#" ng-click="vm.toggleSyllabus($index)" class="pill">Syllabus</a>
          </div>

          <div ng-if="course.showSyllabus" style="margin-top:0.8rem;background:rgba(255,255,255,0.01);padding:0.8rem;border-radius:8px">
            <strong>Syllabus highlights</strong>
            <ul style="margin:6px 0 0 18px;color:var(--muted)">
              <li ng-repeat="item in course.syllabus">{{item}}</li>
            </ul>
          </div>
        </article>
      </div>
    </section>

    <!-- CERTIFICATIONS -->
    <section id="certificates">
      <h2 class="section-title">Certification Guidance</h2>
      <div class="card">
        <p class="muted">We map every course to RedHat certification objectives and provide mock-exams, labs, and exam strategy sessions. Typical certifications covered:</p>
        <ul style="margin-top:0.6rem;color:var(--muted)">
          <li>RHCSA (Red Hat Certified System Administrator)</li>
          <li>RHCE (Red Hat Certified Engineer)</li>
          <li>Red Hat Certified Specialist in Ansible Automation</li>
          <li>Red Hat Certified Specialist in OpenShift Administration</li>
        </ul>
      </div>
    </section>

    <!-- ABOUT -->
    <section id="about">
      <h2 class="section-title">About Longiceps</h2>
      <div class="card">
        <p><strong>Longiceps</strong> is built to help IT professionals and system administrators transition from day-to-day operations to certified, automation-first engineers. Our trainers are experienced practitioners with RedHat-aligned curricula and real-world lab scenarios.</p>
        <p class="muted">We deliver corporate training, public cohorts, and self-paced labs. If you're hiring, we also offer custom training for teams and upskilling programs.</p>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact">
      <h2 class="section-title">Contact & Enroll</h2>
      <div class="card" style="display:grid;grid-template-columns:1fr 360px;gap:1rem">
        <div>
          <form name="contactForm" ng-submit="vm.submit(contactForm)" novalidate>
            <div style="margin-bottom:0.6rem">
              <label class="muted">Full name</label>
              <input name="name" ng-model="vm.form.name" required placeholder="Your full name" />
            </div>
            <div style="margin-bottom:0.6rem">
              <label class="muted">Email</label>
              <input name="email" type="email" ng-model="vm.form.email" required placeholder="you@company.com" />
            </div>
            <div style="margin-bottom:0.6rem">
              <label class="muted">Interested course</label>
              <select ng-model="vm.form.course" ng-options="c.title for c in vm.courses" required>
                <option value="">Choose a course</option>
              </select>
            </div>
            <div style="margin-bottom:0.6rem">
              <label class="muted">Message</label>
              <textarea ng-model="vm.form.message" placeholder="Any questions or request for syllabus" ></textarea>
            </div>

            <div style="display:flex;gap:0.6rem;align-items:center">
              <button type="submit" class="btn" ng-disabled="contactForm.$invalid">Send request</button>
              <div class="muted" style="font-size:13px">We will reply via email within 24-48 hours.</div>
            </div>
          </form>

          <div ng-if="vm.sent" style="margin-top:0.8rem;padding:0.8rem;background:rgba(79,70,229,0.08);border-radius:8px">
            <strong>Thanks — we've received your request.</strong>
            <div class="muted">Our team will contact you to confirm cohort details and payment options.</div>
          </div>
        </div>

        <aside style="padding-left:0.6rem">
          <h3 style="margin-top:0">Contact</h3>
          <div class="muted">Email: <a href="mailto:hello@longiceps.example">hello@longiceps.example</a></div>
          <div class="muted">Phone: +91-XXXXXXXXXX (WhatsApp)</div>
          <div style="margin-top:0.8rem">
            <h4 style="margin:0">Training formats</h4>
            <ul class="muted" style="margin-top:6px">
              <li>Live instructor-led (remote)</li>
              <li>Corporate on-site workshops</li>
              <li>Self-paced labs & sandbox</li>
            </ul>
          </div>
        </aside>

      </div>
    </section>

    <footer>
      <div class="footer-grid">
        <div class="col">
          <div style="font-weight:700">Longiceps</div>
          <div class="muted">RedHat curriculum — Linux · Ansible · OpenShift</div>
        </div>
        <div class="col">
          <div style="font-weight:600">Links</div>
          <div class="muted"><a href="#courses">Courses</a><br><a href="#certificates">Certifications</a></div>
        </div>
        <div class="col">
          <div style="font-weight:600">Follow</div>
          <div class="muted">LinkedIn · Twitter · YouTube (add links when ready)</div>
        </div>
      </div>

      <div style="margin-top:1rem;color:var(--muted);font-size:13px">© Longiceps · All rights reserved</div>
    </footer>

  </main>

  <script>
    angular.module('LongicepsApp', [])
    .controller('MainCtrl', ['$scope', '$timeout', function($scope, $timeout){
      var vm = this;

      vm.openNav = false;

      vm.cohorts = [
        {title:'RHCSA Prep - Weekend Cohort', start: new Date().setDate(new Date().getDate()+14), desc:'6 weeks · Evenings (UTC) — hands-on labs and mock exam.'},
        {title:'Ansible Automation Bootcamp', start: new Date().setDate(new Date().getDate()+21), desc:'4 weeks · Deep dive on playbooks, modules, and pipelines.'},
        {title:'OpenShift Administrator', start: new Date().setDate(new Date().getDate()+35), desc:'5 weeks · Deploy, manage, and scale OpenShift clusters.'}
      ];

      vm.courses = [
        {title:'Linux Administration (RHCSA)', level:'Beginner → Intermediate', duration:'6 weeks', mode:'Live', seats:12, description:'Learn core Linux administration skills, storage, users, networking, and troubleshooting aligned to RHCSA objectives.', syllabus:["Systemd & services","User & group management","Filesystems & LVM","Networking","Security & SELinux"]},
        {title:'Ansible Automation', level:'Intermediate', duration:'4 weeks', mode:'Live', seats:12, description:'Write playbooks, use roles, inventory, and integrate Ansible with CI/CD and real-world workflows.', syllabus:["Playbooks & modules","Roles & Galaxy","Vault & security","Ansible Tower basics","Automation testing"]},
        {title:'OpenShift Container Platform', level:'Intermediate → Advanced', duration:'5 weeks', mode:'Live', seats:10, description:'Hands-on OpenShift: projects, operators, storage, routing, and cluster administration for production.', syllabus:["Cluster install & admin","Workloads & operators","Storage & CI/CD","Networking & security","Cluster troubleshooting"]}
      ];

      vm.toggleSyllabus = function(i){
        vm.courses[i].showSyllabus = !vm.courses[i].showSyllabus;
      }

      vm.form = {};
      vm.sent = false;

      vm.submit = function(form){
        if(form.$invalid) return;
        // Since this is a static site, we can't actually send mail. Simulate success.
        vm.sent = true;
        // reset form after small delay
        $timeout(function(){
          vm.form = {};
          form.$setPristine();
          form.$setUntouched();
        }, 1200);
      };

    }]);
  </script>
</body>
</html>
