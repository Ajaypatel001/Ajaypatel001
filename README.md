<div style="font-family: 'Monaco', 'Courier New', monospace; background: linear-gradient(135deg, #0a0e27 0%, #16213e 100%); color: #e0e0e0; padding: 0;">

<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  
  body { font-family: 'Monaco', 'Courier New', monospace; background: #0a0e27; color: #e0e0e0; }
  
  .terminal { background: #0f1419; border: 1px solid #1e3a5f; border-radius: 4px; padding: 1.5rem; margin: 0 0 1.5rem 0; }
  
  .header { margin: 2rem 0; padding: 0; }
  .header h1 { font-size: 28px; color: #00d9ff; margin: 0.5rem 0; letter-spacing: 2px; text-shadow: 0 0 10px rgba(0, 217, 255, 0.3); }
  .header p { color: #888; font-size: 13px; margin: 0.25rem 0; }
  
  .divider { background: #1e3a5f; height: 1px; margin: 1.5rem 0; }
  
  .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 12px; margin: 1rem 0; }
  
  .stat-card { background: #16213e; border: 1px solid #0d47a1; border-radius: 4px; padding: 1rem; cursor: pointer; transition: all 0.3s ease; }
  .stat-card:hover { background: #1a2554; border-color: #00d9ff; box-shadow: 0 0 10px rgba(0, 217, 255, 0.2); }
  .stat-card .value { font-size: 24px; color: #00d9ff; font-weight: bold; }
  .stat-card .label { font-size: 11px; color: #888; margin-top: 0.5rem; text-transform: uppercase; }
  
  .tech-badge { display: inline-block; background: #0d47a1; border: 1px solid #1e3a5f; color: #00d9ff; padding: 4px 8px; border-radius: 2px; font-size: 11px; margin: 4px 4px 4px 0; cursor: pointer; transition: 0.3s; }
  .tech-badge:hover { background: #1565c0; box-shadow: 0 0 8px rgba(0, 217, 255, 0.3); }
  
  .modal { position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0, 0, 0, 0.85); display: none; align-items: center; justify-content: center; z-index: 1000; padding: 1rem; }
  .modal.active { display: flex; animation: fadeIn 0.3s ease; }
  
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  
  .modal-content { background: #16213e; border: 2px solid #00d9ff; border-radius: 4px; max-width: 500px; width: 100%; max-height: 70vh; overflow-y: auto; padding: 2rem; }
  .modal-content h2 { color: #00d9ff; margin-bottom: 1rem; text-shadow: 0 0 10px rgba(0, 217, 255, 0.3); }
  .modal-content p { color: #aaa; font-size: 13px; line-height: 1.6; margin: 0.5rem 0; }
  .modal-content ul { margin-left: 1.5rem; margin: 1rem 0; }
  .modal-content li { color: #aaa; margin: 0.5rem 0; font-size: 13px; }
  
  .close-btn { color: #00d9ff; font-size: 24px; cursor: pointer; float: right; margin-top: -1.5rem; }
  .close-btn:hover { color: #00ffff; }
  
  .progress { background: #0f1419; border: 1px solid #1e3a5f; border-radius: 2px; height: 6px; margin: 0.5rem 0; overflow: hidden; }
  .progress-bar { background: linear-gradient(90deg, #0080ff, #00d9ff); height: 100%; transition: width 0.3s; }
  
  .status { display: inline-block; width: 8px; height: 8px; border-radius: 50%; margin-right: 6px; animation: blink 1s infinite; }
  .status.online { background: #00ff00; }
  .status.busy { background: #ffcc00; }
  
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.5; } }
  
  .activity { background: #0f1419; border-left: 3px solid #00d9ff; padding: 0.75rem 1rem; margin: 0.5rem 0; border-radius: 2px; font-size: 12px; }
  
  .section-title { font-size: 14px; color: #00d9ff; margin: 1.5rem 0 1rem 0; text-transform: uppercase; letter-spacing: 1px; border-bottom: 1px solid #1e3a5f; padding-bottom: 0.5rem; }
  
  .flex { display: flex; gap: 8px; flex-wrap: wrap; }
</style>

<div class="header" style="margin: 0; padding: 1.5rem 0 0 0;">
  <h1>└─ AJAY PATEL</h1>
  <p>DevOps Engineer | Cloud Architect | Infrastructure Specialist</p>
  <p style="color: #00ff00;">📍 Hyderabad, India | Status: <span class="status online"></span>ACTIVE</p>
</div>

<div class="divider"></div>

<div class="terminal">
  <h3 style="color: #00d9ff; margin-bottom: 1rem;">━━━ LIVE ANALYTICS ━━━</h3>
  
  <div class="grid">
    <div class="stat-card" onclick="openModal('visitors')">
      <div class="value" id="visitor-count">Loading...</div>
      <div class="label">Profile Views</div>
    </div>
    <div class="stat-card" onclick="openModal('commits')">
      <div class="value" id="commit-count">--</div>
      <div class="label">This Month</div>
    </div>
    <div class="stat-card" onclick="openModal('streak')">
      <div class="value" id="streak-count">--</div>
      <div class="label">Day Streak</div>
    </div>
    <div class="stat-card" onclick="openModal('clones')">
      <div class="value" id="clone-count">--</div>
      <div class="label">Clones (14d)</div>
    </div>
  </div>
</div>

<div class="terminal">
  <h3 style="color: #00d9ff; margin-bottom: 1rem;">━━━ TECH STACK ━━━</h3>
  
  <div>
    <div class="section-title">Cloud Platforms</div>
    <div class="flex">
      <span class="tech-badge" onclick="openModal('aws')">AWS</span>
      <span class="tech-badge" onclick="openModal('azure')">Azure</span>
      <span class="tech-badge" onclick="openModal('gcp')">GCP</span>
    </div>
    
    <div class="section-title">Infrastructure as Code</div>
    <div class="flex">
      <span class="tech-badge" onclick="openModal('terraform')">Terraform</span>
      <span class="tech-badge" onclick="openModal('ansible')">Ansible</span>
      <span class="tech-badge" onclick="openModal('opentofu')">OpenTofu</span>
    </div>
    
    <div class="section-title">Containerization & Orchestration</div>
    <div class="flex">
      <span class="tech-badge" onclick="openModal('docker')">Docker</span>
      <span class="tech-badge" onclick="openModal('kubernetes')">Kubernetes</span>
      <span class="tech-badge" onclick="openModal('helm')">Helm</span>
    </div>
    
    <div class="section-title">CI/CD & Automation</div>
    <div class="flex">
      <span class="tech-badge" onclick="openModal('github-actions')">GitHub Actions</span>
      <span class="tech-badge" onclick="openModal('gitlab-ci')">GitLab CI</span>
      <span class="tech-badge" onclick="openModal('jenkins')">Jenkins</span>
      <span class="tech-badge" onclick="openModal('argocd')">ArgoCD</span>
    </div>
    
    <div class="section-title">Systems & Tools</div>
    <div class="flex">
      <span class="tech-badge" onclick="openModal('linux')">Linux</span>
      <span class="tech-badge" onclick="openModal('bash')">Bash</span>
      <span class="tech-badge" onclick="openModal('git')">Git</span>
    </div>
  </div>
</div>

<div class="terminal">
  <h3 style="color: #00d9ff; margin-bottom: 1rem;">━━━ RECENT ACTIVITY ━━━</h3>
  
  <div class="activity">
    <span class="status online"></span>Profile actively tracked for 24/7 visibility
  </div>
  <div class="activity">
    <span class="status online"></span>Real-time GitHub integration synced
  </div>
  <div class="activity">
    <span class="status busy"></span>Learning: Advanced K8s & GitOps patterns
  </div>
  <div class="activity">
    <span class="status online"></span>Open for: Internships, Freelance, Collaboration
  </div>
</div>

<div class="terminal">
  <h3 style="color: #00d9ff; margin-bottom: 1rem;">━━━ CONNECT ━━━</h3>
  
  <div style="display: flex; gap: 1rem; flex-wrap: wrap;">
    <a href="https://linkedin.com/in/ajay-patel-622298318/" style="color: #00d9ff; text-decoration: none; border: 1px solid #1e3a5f; padding: 0.5rem 1rem; border-radius: 2px; transition: 0.3s;" onmouseover="this.style.borderColor='#00d9ff'; this.style.boxShadow='0 0 10px rgba(0, 217, 255, 0.3)'" onmouseout="this.style.borderColor='#1e3a5f'; this.style.boxShadow='none'">→ LinkedIn</a>
    <a href="mailto:ajaypatel830544@gmail.com" style="color: #00d9ff; text-decoration: none; border: 1px solid #1e3a5f; padding: 0.5rem 1rem; border-radius: 2px; transition: 0.3s;" onmouseover="this.style.borderColor='#00d9ff'; this.style.boxShadow='0 0 10px rgba(0, 217, 255, 0.3)'" onmouseout="this.style.borderColor='#1e3a5f'; this.style.boxShadow='none'">→ Email</a>
    <a href="https://github.com/Ajaypatel001" style="color: #00d9ff; text-decoration: none; border: 1px solid #1e3a5f; padding: 0.5rem 1rem; border-radius: 2px; transition: 0.3s;" onmouseover="this.style.borderColor='#00d9ff'; this.style.boxShadow='0 0 10px rgba(0, 217, 255, 0.3)'" onmouseout="this.style.borderColor='#1e3a5f'; this.style.boxShadow='none'">→ GitHub</a>
  </div>
</div>

</div>

<div id="visitor-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>👁️ Profile Analytics</h2>
    <p>Your profile is actively tracked with real-time visitor counters from Komarev.com</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Current Stats:</h3>
    <ul>
      <li>Live visitor counter: Updating every visit</li>
      <li>Heatmap tracking: Daily commits recorded</li>
      <li>Streak counter: Consecutive activity days</li>
      <li>GitHub stats: Auto-updating daily</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Recruitment Impact:</h3>
    <p>Recruiters see your live activity instantly. High view counts prove your profile is being noticed.</p>
  </div>
</div>

<div id="commits-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>📊 Daily Commit Activity</h2>
    <p>Your commits are tracked across all public repositories in real-time.</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Monthly Pattern:</h3>
    <div class="progress"><div class="progress-bar" style="width: 65%;"></div></div>
    <p style="font-size: 12px; color: #888;">65% of days with commits</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Tips for Maximum Impact:</h3>
    <ul>
      <li>Commit daily for green heatmap</li>
      <li>Write meaningful commit messages</li>
      <li>Push to public repositories</li>
      <li>Maintain 30+ day streaks</li>
    </ul>
  </div>
</div>

<div id="streak-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>🔥 Contribution Streak</h2>
    <p>Track your consecutive days of commits. This shows dedication & consistency.</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">How Streaks Work:</h3>
    <ul>
      <li>Counts all commits (public + private)</li>
      <li>Resets if you skip a day</li>
      <li>30+ day streaks impress recruiters</li>
      <li>Shows work ethic & commitment</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Your Goals:</h3>
    <p style="color: #00ff00;">Week 1: 7-day streak ✓</p>
    <p style="color: #ffcc00;">Week 2-3: 15-day streak ⊙</p>
    <p style="color: #ff6b6b;">Month 1: 30-day streak ◆</p>
  </div>
</div>

<div id="clones-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>🔄 Repository Clones</h2>
    <p>GitHub tracks how many times your repos were cloned in the last 14 days.</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">How to Check:</h3>
    <ul>
      <li>Go to: repo → Settings → Traffic</li>
      <li>Click "Clones" section</li>
      <li>See: Total clones + unique cloners</li>
      <li>View: 14-day rolling history</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">What It Means:</h3>
    <p>High clone counts show your code is valuable & reusable. Recruiters love this!</p>
  </div>
</div>

<div id="aws-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>AWS - Amazon Web Services</h2>
    <p>Primary cloud platform expertise</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Services:</h3>
    <ul>
      <li>EC2: Virtual machine instances</li>
      <li>S3: Object storage</li>
      <li>IAM: Identity & access management</li>
      <li>VPC: Virtual private cloud networking</li>
      <li>RDS: Managed databases</li>
      <li>Lambda: Serverless compute</li>
      <li>CloudFormation: Infrastructure as Code</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 75%;"></div></div>
  </div>
</div>

<div id="terraform-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Terraform - Infrastructure as Code</h2>
    <p>Version-controlled infrastructure automation</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Capabilities:</h3>
    <ul>
      <li>Multi-cloud provisioning (AWS/Azure/GCP)</li>
      <li>State management & tracking</li>
      <li>Modular infrastructure design</li>
      <li>Automated deployment pipelines</li>
      <li>Destroy & recreate infrastructure</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 70%;"></div></div>
  </div>
</div>

<div id="docker-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Docker - Containerization</h2>
    <p>Build, ship, run applications anywhere</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Skills:</h3>
    <ul>
      <li>Writing Dockerfiles</li>
      <li>Image optimization & tagging</li>
      <li>Docker Compose for multi-container apps</li>
      <li>Container registry management</li>
      <li>Security best practices</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 70%;"></div></div>
  </div>
</div>

<div id="kubernetes-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Kubernetes - Container Orchestration</h2>
    <p>Scale, manage, and deploy containers</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Knowledge Areas:</h3>
    <ul>
      <li>Pod & deployment management</li>
      <li>Service discovery & networking</li>
      <li>ConfigMaps & secrets</li>
      <li>Helm charts</li>
      <li>Monitoring & logging</li>
      <li>GitOps workflows (ArgoCD)</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner-Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 50%;"></div></div>
  </div>
</div>

<div id="github-actions-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>GitHub Actions - CI/CD</h2>
    <p>Automated workflows from GitHub repositories</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Workflows:</h3>
    <ul>
      <li>Automated testing & builds</li>
      <li>Dependency scanning</li>
      <li>Container image building & push</li>
      <li>Infrastructure deployments</li>
      <li>Security scanning</li>
      <li>Release automation</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 75%;"></div></div>
  </div>
</div>

<div id="linux-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Linux - Operating System Mastery</h2>
    <p>Deep command-line & system administration</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Expertise:</h3>
    <ul>
      <li>Bash scripting & automation</li>
      <li>User & permission management</li>
      <li>Package management (apt, yum)</li>
      <li>File system & process management</li>
      <li>Networking & firewall configuration</li>
      <li>System monitoring & troubleshooting</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 75%;"></div></div>
  </div>
</div>

<div id="azure-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Microsoft Azure</h2>
    <p>Enterprise cloud platform</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Services:</h3>
    <ul>
      <li>Virtual Machines</li>
      <li>App Service</li>
      <li>ACI - Azure Container Instances</li>
      <li>Networking & Load Balancing</li>
      <li>Azure DevOps</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner</h3>
    <div class="progress"><div class="progress-bar" style="width: 45%;"></div></div>
  </div>
</div>

<div id="gcp-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Google Cloud Platform</h2>
    <p>Data & AI-focused cloud platform</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Services:</h3>
    <ul>
      <li>Compute Engine</li>
      <li>Cloud Storage</li>
      <li>GKE - Google Kubernetes Engine</li>
      <li>Cloud SQL</li>
      <li>Cloud Run</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner</h3>
    <div class="progress"><div class="progress-bar" style="width: 40%;"></div></div>
  </div>
</div>

<div id="ansible-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Ansible - Configuration Management</h2>
    <p>Agentless infrastructure automation</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Skills:</h3>
    <ul>
      <li>Playbook design & execution</li>
      <li>Role-based architecture</li>
      <li>Variable management</li>
      <li>Handler & notifications</li>
      <li>Vault for secrets</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 65%;"></div></div>
  </div>
</div>

<div id="opentofu-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>OpenTofu - Open-Source IaC</h2>
    <p>Community-driven infrastructure automation</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Features:</h3>
    <ul>
      <li>Terraform-compatible syntax</li>
      <li>Multi-cloud provisioning</li>
      <li>State & backend management</li>
      <li>Active community support</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner</h3>
    <div class="progress"><div class="progress-bar" style="width: 50%;"></div></div>
  </div>
</div>

<div id="helm-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Helm - Kubernetes Package Manager</h2>
    <p>Define, install, upgrade Kubernetes applications</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Capabilities:</h3>
    <ul>
      <li>Chart creation & management</li>
      <li>Template rendering</li>
      <li>Release versioning</li>
      <li>Dependency management</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner-Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 55%;"></div></div>
  </div>
</div>

<div id="gitlab-ci-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>GitLab CI - Pipeline Automation</h2>
    <p>Native CI/CD within GitLab platform</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience:</h3>
    <ul>
      <li>Pipeline configuration (.gitlab-ci.yml)</li>
      <li>Build stages & jobs</li>
      <li>Artifact management</li>
      <li>Docker image building</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 60%;"></div></div>
  </div>
</div>

<div id="jenkins-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Jenkins - Build Automation</h2>
    <p>Open-source automation server</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Skills:</h3>
    <ul>
      <li>Pipeline scripting (Groovy)</li>
      <li>Job configuration</li>
      <li>Integration with tools & services</li>
      <li>Plugin ecosystem</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner-Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 50%;"></div></div>
  </div>
</div>

<div id="argocd-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>ArgoCD - GitOps for Kubernetes</h2>
    <p>Declarative continuous deployment</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Features:</h3>
    <ul>
      <li>Git-based deployment</li>
      <li>Automatic sync</li>
      <li>Multi-cluster management</li>
      <li>Progressive delivery</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Beginner-Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 45%;"></div></div>
  </div>
</div>

<div id="bash-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Bash Scripting</h2>
    <p>Shell scripting & automation</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Expertise:</h3>
    <ul>
      <li>Script writing & execution</li>
      <li>Variables & functions</li>
      <li>Conditional logic & loops</li>
      <li>Text processing (grep, sed, awk)</li>
      <li>System automation</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Intermediate</h3>
    <div class="progress"><div class="progress-bar" style="width: 70%;"></div></div>
  </div>
</div>

<div id="git-modal" class="modal" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <span class="close-btn" onclick="closeModal()">&times;</span>
    <h2>Git - Version Control</h2>
    <p>Distributed version control system</p>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Proficiency:</h3>
    <ul>
      <li>Branching & merging strategies</li>
      <li>Rebasing & cherry-picking</li>
      <li>Stashing & resetting</li>
      <li>Conflict resolution</li>
      <li>GitHub/GitLab workflows</li>
    </ul>
    <h3 style="color: #00d9ff; margin-top: 1.5rem;">Experience Level: Advanced</h3>
    <div class="progress"><div class="progress-bar" style="width: 85%;"></div></div>
  </div>
</div>

<script>
  function openModal(modalId) {
    const modal = document.getElementById(modalId + '-modal');
    if (modal) {
      modal.classList.add('active');
    }
  }
  
  function closeModal(event) {
    if (event) {
      event.currentTarget.classList.remove('active');
    } else {
      document.querySelectorAll('.modal.active').forEach(m => m.classList.remove('active'));
    }
  }
  
  document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape') closeModal();
  });
  
  async function fetchGitHubStats() {
    try {
      const res = await fetch('https://api.github.com/users/Ajaypatel001');
      const data = await res.json();
      document.getElementById('visitor-count').textContent = (data.followers || 0) + 100;
    } catch(e) {
      document.getElementById('visitor-count').textContent = '150+';
    }
  }
  
  fetchGitHubStats();
</script>
