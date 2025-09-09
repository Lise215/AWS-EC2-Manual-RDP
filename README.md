<!--# AWS-EC2-Setup1-->
#  Manual AWS EC2 Instance Configuration + RDP Connection
Tutorial of manual AWS EC2 Windows Server Setup on MacOS. Terraform tutorial coming soon.

<h2>Tools Used:</h2>
<ul>
  <li> AWS Cloud EC2 Instance </li>
  <li> RDP Cient <a href="https://apps.apple.com/us/app/windows-app/id1295203466?mt=12"> (Microsoft Windows App)</a> </li>
</ul>

<h2>Prerequisites:</h2>
<ul>
  <li> AWS account </li> 
  <li> Basic knowledge of AWS Console </li> 
  <li> RDP client (e.g., Microsoft Windows App for macOS) </li> 
</ul>

<h2>Configuration:</h2>
<ul>
  <li> Region: us-east-1d </li> 
  <li> Instance Type: t3.micro </li> 
  <li> AMI: Windows Server 2025 Base</li> 
</ul>

<h2>Creation Steps:</h2>
<ol>
<li> Login to <a href ="https://signin.aws.amazon.com/signin?client_id=arn%3Aaws%3Asignin%3A%3A%3Aconsole%2Fcanvas&redirect_uri=https%3A%2F%2Fconsole.aws.amazon.com%2Fconsole%2Fhome%3FhashArgs%3D%2523%26isauthcode%3Dtrue%26nc2%3Dh_si%26oauthStart%3D1757439904946%26src%3Dheader-signin%26state%3DhashArgsFromTB_us-east-2_72553320f67b8000&page=resolve&code_challenge=wDtlZBsvJYd16yZgxiI0qHYLvUEeR1W4zT7NJ8j-cIc&code_challenge_method=SHA-256&backwards_compatible=true" target="_blank">AWS Console</a> > All Services > EC2 (under Compute) </li>
<li> Click “Launch Instance” </li>
<li> Select AMI: Windows Server 2025 Base </li>
<li> Choose Instance Type: t2.micro or t3.micro (Free Tier) </li>
<li> Configure instance: </li>
<ul>  
    <li> Network: default VPC </li> 
    <li> Subnet: Choose one </li> 
    <li> Security Group: (default is fine) </li> 
</ul>
<li> Add storage (keep default) </li>
<li> Add tags (e.g., Name: MyEC2Instance) </li>
<li> Configure security group: </li>
  <ul>  
    <li> Allow RDP (port 3389) from your IP </li>
<li> Select a key pair (or create one) and save credentials securely on device </li>
<li> Review settings and click "Launch" </li>
    <ul>  
    <li> Wait for the instance to reach "running" status </li>
</ol>

<h2>Connecting Steps (RDP):</h2>
<ol>
    <li> Select your instance</li>
    <li> Click Actions > Security > Get Windows Password</li>
    <li> Upload your `.pem` key file</li>
    <li> Decrypt password and copy it</li>
    <li> Open Remote Desktop client </li>
    <li> Enter Public IPv4 address of instance</li>
    <li> Enter Credentials: </li>
            <i>Username: <i>'Administrator' </i><br>
            <i>Password: (the one that you just decrypted)</i></li>
    <li> Accept security prompt and connect</li>
</ol>
              
<h2> </h2>
<h2>Best Practices:</h2>

- Elastic IP: Allocate and associate an Elastic IP to keep a static IP
- Tags: Add tags like `Name=MyWindowsServer`
- Backup: Create snapshots regularly
- Security: Avoid exposing RDP to all IPs (`0.0.0.0/0`)
- Stop or terminate the instance when not in use to avoid financial charges
- Delete unused Elastic IPs and volumes
