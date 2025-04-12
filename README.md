# Donation Platform Website using W3.CSS Startup Template

I'll create a comprehensive donation platform website based on your requirements using the W3.CSS Startup template. This implementation will include all 8 functions you mentioned plus the accessibility features and motivation system.

## Complete Code Implementation

```html
<!DOCTYPE html>
<html lang="en">
<head>
<title>GiveHope - Donation Platform</title>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Raleway">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
body,h1,h2,h3,h4,h5,h6 {font-family: "Raleway", sans-serif}
body, html {
  height: 100%;
  line-height: 1.8;
}
.w3-bar .w3-button {
  padding: 16px;
}
.chart-container {
  position: relative;
  margin: auto;
  height: 300px;
  width: 100%;
}
.donation-progress {
  height: 30px;
  margin: 15px 0;
}
.lite-mode {
  font-size: 18px !important;
}
.lite-mode .w3-button {
  padding: 20px !important;
  font-size: 18px !important;
}
.lite-mode .w3-card {
  border: 2px solid #000 !important;
}
.offline-mode {
  background-color: #f5f5f5 !important;
}
.offline-mode img {
  display: none !important;
}
</style>
</head>
<body>

<!-- Navbar (sit on top) -->
<div class="w3-top">
  <div class="w3-bar w3-white w3-card" id="myNavbar">
    <a href="#home" class="w3-bar-item w3-button w3-wide">GIVEHOPE</a>
    <!-- Right-sided navbar links -->
    <div class="w3-right w3-hide-small">
      <a href="#dashboard" class="w3-bar-item w3-button"><i class="fa fa-home"></i> Dashboard</a>
      <a href="#donate" class="w3-bar-item w3-button"><i class="fa fa-heart"></i> Donate</a>
      <a href="#history" class="w3-bar-item w3-button"><i class="fa fa-history"></i> History</a>
      <a href="#rewards" class="w3-bar-item w3-button"><i class="fa fa-gift"></i> Rewards</a>
      <a href="#settings" class="w3-bar-item w3-button"><i class="fa fa-cog"></i> Settings</a>
      <a href="#" class="w3-bar-item w3-button" onclick="toggleLiteMode()"><i class="fa fa-eye"></i> Lite Mode</a>
      <a href="#" class="w3-bar-item w3-button" onclick="toggleOfflineMode()"><i class="fa fa-plug"></i> Offline</a>
    </div>
    <!-- Hide right-floated links on small screens and replace them with a menu icon -->
    <a href="javascript:void(0)" class="w3-bar-item w3-button w3-right w3-hide-large w3-hide-medium" onclick="w3_open()">
      <i class="fa fa-bars"></i>
    </a>
  </div>
</div>

<!-- Sidebar on small screens when clicking the menu icon -->
<nav class="w3-sidebar w3-bar-block w3-black w3-card w3-animate-left w3-hide-medium w3-hide-large" style="display:none" id="mySidebar">
  <a href="javascript:void(0)" onclick="w3_close()" class="w3-bar-item w3-button w3-large w3-padding-16">Close ×</a>
  <a href="#dashboard" onclick="w3_close()" class="w3-bar-item w3-button">Dashboard</a>
  <a href="#donate" onclick="w3_close()" class="w3-bar-item w3-button">Donate</a>
  <a href="#history" onclick="w3_close()" class="w3-bar-item w3-button">History</a>
  <a href="#rewards" onclick="w3_close()" class="w3-bar-item w3-button">Rewards</a>
  <a href="#settings" onclick="w3_close()" class="w3-bar-item w3-button">Settings</a>
  <a href="#" onclick="toggleLiteMode(); w3_close()" class="w3-bar-item w3-button">Lite Mode</a>
  <a href="#" onclick="toggleOfflineMode(); w3_close()" class="w3-bar-item w3-button">Offline Mode</a>
</nav>

<!-- Header with full-height image -->
<header class="bgimg-1 w3-display-container w3-grayscale-min" id="home">
  <div class="w3-display-left w3-text-white" style="padding:48px">
    <span class="w3-jumbo w3-hide-small">Make a Difference Today</span><br>
    <span class="w3-xxlarge w3-hide-large w3-hide-medium">Make a Difference Today</span><br>
    <span class="w3-large">Join our community of givers and help transform lives through your donations.</span>
    <p><a href="#donate" class="w3-button w3-white w3-padding-large w3-large w3-margin-top w3-opacity w3-hover-opacity-off">Donate Now</a></p>
  </div> 
</header>

<!-- Dashboard Section -->
<div class="w3-container w3-light-grey" style="padding:128px 16px" id="dashboard">
  <h3 class="w3-center">YOUR DONATION DASHBOARD</h3>
  <p class="w3-center w3-large">Overview of your giving activities</p>
  
  <div class="w3-row-padding" style="margin-top:64px">
 
    <!-- Balance Card -->
    <div class="w3-col l3 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Account Balance</h3>
          <p class="w3-center w3-xxlarge">RM <span id="accountBalance">150.00</span></p>
          <button onclick="document.getElementById('topupModal').style.display='block'" class="w3-button w3-block w3-green">Top Up</button>
        </div>
      </div>
    </div>
    
    <!-- Points Card -->
    <div class="w3-col l3 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Your Points</h3>
          <p class="w3-center w3-xxlarge"><span id="userPoints">150</span> pts</p>
          <button onclick="document.getElementById('rewardsModal').style.display='block'" class="w3-button w3-block w3-blue">Redeem Rewards</button>
        </div>
      </div>
    </div>
    
    <!-- Recent Donation -->
    <div class="w3-col l3 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Recent Donation</h3>
          <div class="w3-panel w3-leftbar w3-light-grey">
            <p><i class="fa fa-quote-right w3-xxlarge w3-opacity"></i><br>
            <i class="fa fa-home w3-large"></i> <strong>Orphanage Food Fund</strong><br>
            <i class="fa fa-calendar"></i> 15 May 2023<br>
            <i class="fa fa-money"></i> RM50.00</p>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Impact Summary -->
    <div class="w3-col l3 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Your Impact</h3>
          <p class="w3-center"><i class="fa fa-cutlery w3-xxlarge"></i><br>15 Meals Provided</p>
          <p class="w3-center"><i class="fa fa-tree w3-xxlarge"></i><br>150 Trees Planted</p>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Charts Section -->
  <div class="w3-row-padding" style="margin-top:32px">
    <div class="w3-col l6 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Monthly Donation Trend</h3>
          <div class="chart-container">

                <!-- News Sidebar -->
    <div class="w3-col l5 m12">
      <div class="w3-card w3-white w3-padding" style="margin-top:16px">
        <h4><b>TRENDING CAUSES</b></h4>
        <div class="w3-panel w3-border-bottom w3-hover-light-grey">
          <h5>Education Fund</h5>
          <p>82% funded | 3 days remaining</p>
          <div class="w3-light-grey">
            <div class="w3-blue" style="height:5px;width:82%"></div>
          </div>
        </div>
        <div class="w3-panel w3-border-bottom w3-hover-light-grey">
          <h5>Disaster Relief</h5>
          <p>45% funded | 12 days remaining</p>
          <div class="w3-light-grey">
            <div class="w3-blue" style="height:5px;width:45%"></div>
          </div>
        </div>
        <div class="w3-panel w3-hover-light-grey">
          <h5>Wildlife Conservation</h5>
          <p>67% funded | 5 days remaining</p>
          <div class="w3-light-grey">
            <div class="w3-blue" style="height:5px;width:67%"></div>
          </div>
        </div>
      </div>
          </div>
        </div>
      </div>
    </div>
    
    <div class="w3-col l6 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container">
          <h3 class="w3-center">Donation Categories</h3>
          <div class="chart-container">
            <canvas id="categoryChart"></canvas>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Donate Section -->
<div class="w3-container" style="padding:128px 16px" id="donate">
  <h3 class="w3-center">MAKE A DONATION</h3>
  <p class="w3-center w3-large">Support causes you care about</p>
  
  <div class="w3-row-padding" style="margin-top:64px">
    <!-- Featured Campaigns -->
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <img src="/w3images/tech.jpg" alt="Education" style="width:100%">
        <div class="w3-container">
          <h4><b>Education for All</b></h4>
          <p>Help underprivileged children access quality education</p>
          
          <div class="w3-light-grey w3-round-xlarge">
            <div class="w3-container w3-blue w3-round-xlarge" style="width:65%">65%</div>
          </div>
          <p>RM65,000 raised of RM100,000 goal</p>
          
          <p><button class="w3-button w3-block w3-blue" onclick="document.getElementById('donateModal').style.display='block';setCampaign('Education for All')">Donate Now</button></p>
        </div>
      </div>
    </div>
    
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <img src="/w3images/tech.jpg" alt="Hunger" style="width:100%">
        <div class="w3-container">
          <h4><b>End Hunger</b></h4>
          <p>Provide meals for families facing food insecurity</p>
          
          <div class="w3-light-grey w3-round-xlarge">
            <div class="w3-container w3-blue w3-round-xlarge" style="width:30%">30%</div>
          </div>
          <p>RM30,000 raised of RM100,000 goal</p>
          
          <p><button class="w3-button w3-block w3-blue" onclick="document.getElementById('donateModal').style.display='block';setCampaign('End Hunger')">Donate Now</button></p>
        </div>
      </div>
    </div>
    
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <img src="/w3images/tech.jpg" alt="Environment" style="width:100%">
        <div class="w3-container">
          <h4><b>Green Earth</b></h4>
          <p>Plant trees and protect our environment</p>
          
          <div class="w3-light-grey w3-round-xlarge">
            <div class="w3-container w3-blue w3-round-xlarge" style="width:80%">80%</div>
          </div>
          <p>RM80,000 raised of RM100,000 goal</p>
          
          <p><button class="w3-button w3-block w3-blue" onclick="document.getElementById('donateModal').style.display='block';setCampaign('Green Earth')">Donate Now</button></p>
        </div>
      </div>
    </div>
  </div>
  
  <!-- More Campaigns Button -->
  <div class="w3-center" style="margin-top:32px">
    <button class="w3-button w3-black w3-padding-large w3-large">View All Campaigns</button>
  </div>
</div>

<!-- History Section -->
<div class="w3-container w3-light-grey" style="padding:128px 16px" id="history">
  <h3 class="w3-center">DONATION HISTORY</h3>
  <p class="w3-center w3-large">Your donation journey</p>
  
  <div class="w3-row-padding" style="margin-top:64px">
    <div class="w3-col m12">
      <div class="w3-card">
        <div class="w3-container w3-padding-16">
          <div class="w3-responsive">
            <table class="w3-table-all">
              <thead>
                <tr class="w3-blue">
                  <th>Date</th>
                  <th>Campaign</th>
                  <th>Organization</th>
                  <th>Amount</th>
                  <th>Method</th>
                  <th>Status</th>
                  <th>Details</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>15 May 2023</td>
                  <td>Orphanage Food Fund</td>
                  <td>Hope for Children</td>
                  <td>RM50.00</td>
                  <td>QR Pay</td>
                  <td><span class="w3-tag w3-green">Completed</span></td>
                  <td><button class="w3-button w3-tiny w3-blue">View</button></td>
                </tr>
                <tr>
                  <td>10 May 2023</td>
                  <td>Education for All</td>
                  <td>Teach Malaysia</td>
                  <td>RM100.00</td>
                  <td>Bank Transfer</td>
                  <td><span class="w3-tag w3-green">Completed</span></td>
                  <td><button class="w3-button w3-tiny w3-blue">View</button></td>
                </tr>
                <tr>
                  <td>5 May 2023</td>
                  <td>Green Earth</td>
                  <td>Eco Warriors</td>
                  <td>RM30.00</td>
                  <td>Credit Card</td>
                  <td><span class="w3-tag w3-green">Completed</span></td>
                  <td><button class="w3-button w3-tiny w3-blue">View</button></td>
                </tr>
                <tr>
                  <td>1 May 2023</td>
                  <td>Flood Relief</td>
                  <td>Malaysian Red Crescent</td>
                  <td>RM20.00</td>
                  <td>QR Pay</td>
                  <td><span class="w3-tag w3-green">Completed</span></td>
                  <td><button class="w3-button w3-tiny w3-blue">View</button></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Export Button -->
  <div class="w3-center" style="margin-top:32px">
    <button class="w3-button w3-black w3-padding-large w3-large">Export History</button>
  </div>
</div>

<!-- Rewards Section -->
<div class="w3-container" style="padding:128px 16px" id="rewards">
  <h3 class="w3-center">REWARDS & IMPACT</h3>
  <p class="w3-center w3-large">Your generosity makes a difference</p>
  
  <div class="w3-row-padding" style="margin-top:64px">
    <!-- Impact Rewards -->
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container w3-center">
          <h3>Plant Trees</h3>
          <div class="w3-panel w3-blue w3-round-large">
            <p class="w3-xxlarge">100 pts</p>
            <p>Plant 1 tree in your name</p>
          </div>
          <p>Partner: Green Earth Malaysia</p>
          <button class="w3-button w3-block w3-green" onclick="redeemReward('Plant a Tree', 100)">Redeem</button>
        </div>
      </div>
    </div>
    
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container w3-center">
          <h3>Feed a Child</h3>
          <div class="w3-panel w3-blue w3-round-large">
            <p class="w3-xxlarge">50 pts</p>
            <p>Provide 1 meal for an orphan</p>
          </div>
          <p>Partner: Hope for Children</p>
          <button class="w3-button w3-block w3-green" onclick="redeemReward('Feed a Child', 50)">Redeem</button>
        </div>
      </div>
    </div>
    
    <div class="w3-col l4 m6 w3-margin-bottom">
      <div class="w3-card">
        <div class="w3-container w3-center">
          <h3>Eco Kit</h3>
          <div class="w3-panel w3-blue w3-round-large">
            <p class="w3-xxlarge">200 pts</p>
            <p>Reusable shopping bag & bottle</p>
          </div>
          <p>Partner: EcoLife</p>
          <button class="w3-button w3-block w3-green" onclick="redeemReward('Eco Kit', 200)">Redeem</button>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Certificates -->
  <div class="w3-row-padding" style="margin-top:64px">
    <div class="w3-col m12">
      <div class="w3-card">
        <div class="w3-container w3-padding-16">
          <h3 class="w3-center">Your Certificates</h3>
          <div class="w3-row-padding">
            <div class="w3-col l4 m6 w3-margin-bottom">
              <div class="w3-card w3-hover-shadow">
                <div class="w3-container w3-center w3-padding-16">
                  <i class="fa fa-certificate w3-jumbo w3-text-amber"></i>
                  <h4>Tree Planter</h4>
                  <p>For planting 100 trees</p>
                  <button class="w3-button w3-blue">View</button>
                  <button class="w3-button w3-green">Download</button>
                </div>
              </div>
            </div>
            <div class="w3-col l4 m6 w3-margin-bottom">
              <div class="w3-card w3-hover-shadow">
                <div class="w3-container w3-center w3-padding-16">
                  <i class="fa fa-certificate w3-jumbo w3-text-amber"></i>
                  <h4>Hope Giver</h4>
                  <p>For donating RM1000</p>
                  <button class="w3-button w3-blue">View</button>
                  <button class="w3-button w3-green">Download</button>
                </div>
              </div>
            </div>
            <div class="w3-col l4 m6 w3-margin-bottom">
              <div class="w3-card w3-hover-shadow">
                <div class="w3-container w3-center w3-padding-16">
                  <i class="fa fa-certificate w3-jumbo w3-text-amber"></i>
                  <h4>Eco Champion</h4>
                  <p>For environmental contributions</p>
                  <button class="w3-button w3-blue">View</button>
                  <button class="w3-button w3-green">Download</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Settings Section -->
<div class="w3-container w3-light-grey" style="padding:128px 16px" id="settings">
  <h3 class="w3-center">SETTINGS</h3>
  <p class="w3-center w3-large">Customize your experience</p>
  
  <div class="w3-row-padding" style="margin-top:64px">
    <div class="w3-col m6">
      <div class="w3-card">
        <div class="w3-container w3-padding-16">
          <h4>Account Settings</h4>
          <form>
            <p><label>Name</label>
            <input class="w3-input w3-border" type="text" value="John Doe"></p>
            
            <p><label>Email</label>
            <input class="w3-input w3-border" type="text" value="john@example.com"></p>
            
            <p><label>Phone</label>
            <input class="w3-input w3-border" type="text" value="+60123456789"></p>
            
            <button type="button" class="w3-button w3-blue">Update Profile</button>
          </form>
        </div>
      </div>
    </div>
    
    <div class="w3-col m6">
      <div class="w3-card">
        <div class="w3-container w3-padding-16">
          <h4>App Preferences</h4>
          
          <div class="w3-section">
            <label class="w3-large">Theme</label>
            <div>
              <button class="w3-button w3-white w3-border">Light</button>
              <button class="w3-button w3-black">Dark</button>
              <button class="w3-button w3-blue">Blue</button>
            </div>
          </div>
          
          <div class="w3-section">
            <label class="w3-large">Font Size</label>
            <div>
              <button class="w3-button w3-white w3-border">Small</button>
              <button class="w3-button w3-white w3-border w3-blue">Medium</button>
              <button class="w3-button w3-white w3-border">Large</button>
            </div>
          </div>
          
          <div class="w3-section">
            <label class="w3-large">Notifications</label>
            <div>
              <input class="w3-check" type="checkbox" checked>
              <label>Email Notifications</label><br>
              <input class="w3-check" type="checkbox" checked>
              <label>Push Notifications</label><br>
              <input class="w3-check" type="checkbox">
              <label>SMS Notifications</label>
            </div>
          </div>
          
          <div class="w3-section">
            <label class="w3-large">Accessibility</label>
            <div>
              <button class="w3-button w3-white w3-border" onclick="toggleLiteMode()">Toggle Lite Mode</button>
              <button class="w3-button w3-white w3-border" onclick="toggleVoiceGuide()">Toggle Voice Guide</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Feedback Form -->
  <div class="w3-row-padding" style="margin-top:32px">
    <div class="w3-col m12">
      <div class="w3-card">
        <div class="w3-container w3-padding-16">
          <h4>Feedback & Suggestions</h4>
          <form>
            <p><label>Subject</label>
            <input class="w3-input w3-border" type="text"></p>
            
            <p><label>Message</label>
            <textarea class="w3-input w3-border" style="height:150px"></textarea></p>
            
            <p><label>Rate Your Experience</label>
            <div class="w3-center">
              <span class="fa fa-star w3-xxlarge w3-hover-text-yellow" onclick="rateStar(1)"></span>
              <span class="fa fa-star w3-xxlarge w3-hover-text-yellow" onclick="rateStar(2)"></span>
              <span class="fa fa-star w3-xxlarge w3-hover-text-yellow" onclick="rateStar(3)"></span>
              <span class="fa fa-star w3-xxlarge w3-hover-text-yellow" onclick="rateStar(4)"></span>
              <span class="fa fa-star w3-xxlarge w3-hover-text-yellow" onclick="rateStar(5)"></span>
            </div></p>
            
            <button type="button" class="w3-button w3-blue">Submit Feedback</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Footer -->
<footer class="w3-center w3-black w3-padding-64">
  <div class="w3-xlarge w3-section">
    <i class="fa fa-facebook-official w3-hover-opacity"></i>
    <i class="fa fa-instagram w3-hover-opacity"></i>
    <i class="fa fa-twitter w3-hover-opacity"></i>
    <i class="fa fa-linkedin w3-hover-opacity"></i>
  </div>
  <p>Powered by <a href="#" title="GiveHope" target="_blank" class="w3-hover-text-green">GiveHope</a></p>
  <p>© 2025 GiveHope Donation Platform. All rights reserved.</p>
</footer>

<!-- Modals -->

<!-- Top Up Modal -->
<div id="topupModal" class="w3-modal">
  <div class="w3-modal-content w3-animate-top w3-card-4">
    <header class="w3-container w3-blue"> 
      <span onclick="document.getElementById('topupModal').style.display='none'" 
      class="w3-button w3-display-topright">&times;</span>
      <h2>Top Up Your Account</h2>
    </header>
    <div class="w3-container">
      <p>Select top up method:</p>
      <div class="w3-row">
        <div class="w3-col s4">
          <div class="w3-card w3-center w3-padding-16 w3-hover-light-grey" onclick="selectTopupMethod('bank')">
            <i class="fa fa-bank w3-xxlarge"></i>
            <p>Bank Transfer</p>
          </div>
        </div>
        <div class="w3-col s4">
          <div class="w3-card w3-center w3-padding-16 w3-hover-light-grey" onclick="selectTopupMethod('card')">
            <i class="fa fa-credit-card w3-xxlarge"></i>
            <p>Credit/Debit Card</p>
          </div>
        </div>
        <div class="w3-col s4">
          <div class="w3-card w3-center w3-padding-16 w3-hover-light-grey" onclick="selectTopupMethod('qr')">
            <i class="fa fa-qrcode w3-xxlarge"></i>
            <p>QR Payment</p>
          </div>
        </div>
      </div>
      
      <div id="bankDetails" style="display:none; margin-top:20px">
        <h4>Bank Transfer Details</h4>
        <p>Bank: Maybank</p>
        <p>Account: 1234567890</p>
        <p>Name: GiveHope Foundation</p>
        <p>Reference: Your mobile number</p>
      </div>
      
      <div id="cardDetails" style="display:none; margin-top:20px">
        <form>
          <p><label>Card Number</label>
          <input class="w3-input w3-border" type="text" placeholder="1234 5678 9012 3456"></p>
          
          <div class="w3-row">
            <div class="w3-col m6">
              <p><label>Expiry Date</label>
              <input class="w3-input w3-border" type="text" placeholder="MM/YY"></p>
            </div>
            <div class="w3-col m6">
              <p><label>CVV</label>
              <input class="w3-input w3-border" type="text" placeholder="123"></p>
            </div>
          </div>
          
          <p><label>Amount (RM)</label>
          <input class="w3-input w3-border" type="number" id="cardAmount" value="50"></p>
          
          <button type="button" class="w3-button w3-blue" onclick="topupAccount('card')">Top Up</button>
        </form>
      </div>
      
      <div id="qrDetails" style="display:none; margin-top:20px">
        <div class="w3-center">
          <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=GiveHopeTopUp12345" alt="QR Code">
          <p>Scan this QR code with your banking app</p>
          <p>Amount: <input class="w3-input w3-border" type="number" id="qrAmount" value="50" style="width:100px; display:inline-block"> RM</p>
        </div>
      </div>
      
      <div id="cashDetails" style="display:none; margin-top:20px">
        <h4>Cash Deposit via Partner Locations</h4>
        <p>You can top up your account with cash at our partner locations:</p>
        <ul>
          <li>7-Eleven stores</li>
          <li>Maybank ATMs (select GiveHope Top Up)</li>
          <li>Participating retail stores</li>
        </ul>
        <p>Please request for a receipt after deposit.</p>
      </div>
    </div>
    <footer class="w3-container w3-light-grey w3-padding">
      <button class="w3-button w3-right w3-blue" onclick="document.getElementById('topupModal').style.display='none'">Close</button>
      <p>Need help? Contact support@givehope.org</p>
    </footer>
  </div>
</div>

<!-- Donate Modal -->
<div id="donateModal" class="w3-modal">
  <div class="w3-modal-content w3-animate-top w3-card-4">
    <header class="w3-container w3-blue"> 
      <span onclick="document.getElementById('donateModal').style.display='none'" 
      class="w3-button w3-display-topright">&times;</span>
      <h2>Make a Donation</h2>
    </header>
    <div class="w3-container">
      <h4 id="donationCampaign">Education for All</h4>
      <p>Organization: <span id="donationOrg">Teach Malaysia</span></p>
      
      <div class="w3-panel w3-light-grey">
        <div class="w3-light-grey w3-round-xlarge">
          <div class="w3-container w3-blue w3-round-xlarge" style="width:65%">65%</div>
        </div>
        <p>RM65,000 raised of RM100,000 goal</p>
      </div>
      
      <p>Select donation amount (RM):</p>
      <div class="w3-row">
        <div class="w3-col s4">
          <button class="w3-button w3-block w3-light-grey w3-margin-bottom" onclick="setDonationAmount(10)">10</button>
        </div>
        <div class="w3-col s4">
          <button class="w3-button w3-block w3-light-grey w3-margin-bottom" onclick="setDonationAmount(50)">50</button>
        </div>
        <div class="w3-col s4">
          <button class="w3-button w3-block w3-light-grey w3-margin-bottom" onclick="setDonationAmount(100)">100</button>
        </div>
      </div>
      
      <p>Or enter custom amount:</p>
      <input class="w3-input w3-border" type="number" id="customAmount" placeholder="Enter amount in RM">
      
      <p>Payment method:</p>
      <select class="w3-select w3-border" id="paymentMethod">
        <option value="" disabled selected>Choose your payment method</option>
        <option value="account">Account Balance</option>
        <option value="card">Credit/Debit Card</option>
        <option value="bank">Bank Transfer</option>
        <option value="qr">QR Payment</option>
        <option value="cash">Cash (via partner locations)</option>
      </select>
      
      <p style="margin-top:20px"><label>Add a message (optional)</label>
      <textarea class="w3-input w3-border" id="donationMessage" placeholder="Your message to the organization"></textarea></p>
      
      <div class="w3-panel w3-pale-blue w3-leftbar w3-border-blue">
        <p>RM1 = 1 point. You'll earn <span id="pointsEarned">0</span> points from this donation!</p>
      </div>
      
      <button class="w3-button w3-block w3-green" onclick="processDonation()">Donate Now</button>
    </div>
  </div>
</div>

<!-- Rewards Modal (Updated with new option) -->
<div id="rewardsModal" class="w3-modal">
  <div class="w3-modal-content w3-animate-top w3-card-4">
    <header class="w3-container w3-blue"> 
      <span onclick="document.getElementById('rewardsModal').style.display='none'" 
      class="w3-button w3-display-topright">&times;</span>
      <h2>Redeem Your Points</h2>
    </header>
    <div class="w3-container">
      <p>Your current points: <strong id="modalPoints">150</strong></p>
      
      <div class="w3-panel w3-light-grey">
        <h4>Impact Rewards</h4>
        <div class="w3-row">
          <div class="w3-col m4">
            <div class="w3-card w3-center w3-padding w3-hover-light-grey" onclick="selectReward('tree', 100)">
              <i class="fa fa-tree w3-xxlarge"></i>
              <p>Plant a Tree (500 pts)</p>
            </div>
          </div>
          <div class="w3-col m4">
            <div class="w3-card w3-center w3-padding w3-hover-light-grey" onclick="selectReward('meal', 50)">
              <i class="fa fa-cutlery w3-xxlarge"></i>
              <p>Feed a Child (50 pts)</p>
            </div>
          </div>
          <div class="w3-col m4">
            <div class="w3-card w3-center w3-padding w3-hover-light-grey" onclick="selectReward('eco', 200)">
              <i class="fa fa-recycle w3-xxlarge"></i>
              <p>Eco Kit (200 pts)</p>
            </div>
          </div>
        </div>
        <!-- ... rest of rewards modal remains the same ... -->
      </div>
    </div>
  </div>
</div>
