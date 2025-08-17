<header *ngIf="router.url==='/userLogin'">
    <div class="header-content">
        <div class="logo">
            <div class="logo-icon">SB</div>
            SecureBank
        </div>
        <nav>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </div>
</header>


   

    <router-outlet></router-outlet>


<footer>
    <div class="footer-content">
        <div class="footer-section">
            <h3>Quick Links</h3>
            <p><a href="#">Online Banking</a></p>
            <p><a href="#">Mobile App</a></p>
            <p><a href="#">Find ATM</a></p>
            <p><a href="#">Customer Support</a></p>
        </div>
        <div class="footer-section">
            <h3>Services</h3>
            <p><a href="#">Personal Banking</a></p>
            <p><a href="#">Business Banking</a></p>
            <p><a href="#">Loans & Credit</a></p>
            <p><a href="#">Investment</a></p>
        </div>
        <div class="footer-section">
            <h3>Contact Info</h3>
            <p>📞 1-800-SECURE-BANK</p>
            <!-- <p>✉️ support@securebank.com</p> -->
            <p>📍 123 Banking Street, Finance City</p>
        </div>
    </div>
    <div class="footer-bottom">
        <p>&copy; 2025 SecureBank. All rights reserved. | Privacy Policy | Terms of Service</p>
    </div>
</footer>

--------------------------------------------------------------------------------------------

import { Component, signal } from '@angular/core';
import { Router, RouterLink, RouterOutlet } from '@angular/router';

@Component({
  selector: 'app-root',
  imports: [RouterOutlet,RouterLink],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
  protected readonly title = signal('05-iNB-bank');
  constructor(public router:Router){}
}
--------------------------------------------------------------------------------------------------
<h1>{{showDetails()}}</h1>
<header>
    <div class="header-content">
        <div class="logo">
            <div class="logo-icon">SB</div>
            SecureBank
        </div>
        <div class="user-info">
            <h1>Welcome, {{showUsername()}}</h1>
            <div class="user-avatar">JD</div>
            <button class="logout-btn" onclick="logout()">Logout</button>
        </div>
    </div>
</header>

<!-- Main Layout -->
<div class="main-layout">
    <!-- Left Sidebar - Dashboard Menu -->
    <nav class="sidebar">
        <div class="sidebar-header">
            <h2>Dashboard</h2>
            <p>Quick access to all services</p>
        </div>

        <div class="menu-section">
            <div class="menu-title">Banking Services</div>
            <a href="#" class="menu-item active" data-section="overview">
                <span class="menu-icon">🏠</span>
                <span>Account Overview</span>
            </a>
            <a href="cheque" class="menu-item" data-section="issue-cheque">
                <span class="menu-icon">📝</span>
                <span>Issue Cheque</span>
            </a>
            <a class="menu-item notification-badge" data-section="pending-cheques" (click)="showAccountNo()" >
                <span class="menu-icon">⏳</span>
                <span>Pending Cheques
                </span>
            </a>
            <a href="#" class="menu-item" data-section="neft">
                <span class="menu-icon">💸</span>
                <span>NEFT Transfer</span>
            </a>
            <a href="#" class="menu-item" data-section="fund-transfer">
                <span class="menu-icon">🔄</span>
                <span>Fund Transfer</span>
            </a>
        </div>

        <div class="menu-section">
            <div class="menu-title">Account Management</div>
            <a href="#" class="menu-item" data-section="statements">
                <span class="menu-icon">📊</span>
                <span>Bank Statements</span>
            </a>
            <a href="#" class="menu-item" data-section="transactions">
                <span class="menu-icon">📋</span>
                <span>Transaction History</span>
            </a>
            <a href="#" class="menu-item" data-section="beneficiaries">
                <span class="menu-icon">👥</span>
                <span>Manage Beneficiaries</span>
            </a>
        </div>

        <div class="menu-section">
            <div class="menu-title">Services</div>
            <a href="#" class="menu-item" data-section="cards">
                <span class="menu-icon">💳</span>
                <span>Cards & ATM</span>
            </a>
            <a href="#" class="menu-item" data-section="loans">
                <span class="menu-icon">🏡</span>
                <span>Loans & Credit</span>
            </a>
            <a href="#" class="menu-item" data-section="investments">
                <span class="menu-icon">📈</span>
                <span>Investments</span>
            </a>
            <a href="#" class="menu-item" data-section="settings">
                <span class="menu-icon">⚙️</span>
                <span>Settings</span>
            </a>
        </div>
    </nav>

    <!-- Right Main Content -->
    <main class="main-content" id="mainContent">
        <!-- Welcome Section -->
        <div class="welcome-section animated">
            <div class="welcome-header">
                <div class="welcome-text">
                    <h1>Good Morning, {{showUsername()}} !</h1>
                    <p>Here's your account summary for today</p>
                </div>
                <div class="current-time" id="currentTime"></div>
            </div>
        </div>

        <!-- Account Overview Cards -->
        <div class="account-overview">
            <div class="account-card animated" style="animation-delay: 0.1s">
                <h3>Savings Account</h3>
                <div class="account-number">Account: ****7892</div>
                <div class="balance">₹2,45,680.50</div>
                <div class="balance-label">Available Balance</div>
            </div>

            <div class="account-card animated" style="animation-delay: 0.2s">
                <h3>Current Account</h3>
                <div class="account-number">Account: ****3456</div>
                <div class="balance">₹8,92,340.25</div>
                <div class="balance-label">Available Balance</div>
            </div>

            <div class="account-card animated" style="animation-delay: 0.3s">
                <h3>Fixed Deposit</h3>
                <div class="account-number">FD: ****9876</div>
                <div class="balance">₹5,00,000.00</div>
                <div class="balance-label">Maturity: Dec 2025</div>
            </div>
        </div>

        <!-- Quick Actions -->
        <div class="quick-actions animated" style="animation-delay: 0.4s">
            <h2 class="section-title">
                <span>⚡</span>
                Quick Actions
            </h2>
            <div class="actions-grid">
                <div class="action-card" onclick="navigateTo('issue-cheque')">
                    <div class="action-icon">📝</div>
                    <div class="action-title">Issue Cheque</div>
                    <div class="action-desc">Create and issue new cheques</div>
                </div>
                <div class="action-card secondary" onclick="navigateTo('neft')">
                    <div class="action-icon">💸</div>
                    <div class="action-title">NEFT Transfer</div>
                    <div class="action-desc">Transfer funds via NEFT</div>
                </div>
                <div class="action-card success" onclick="navigateTo('fund-transfer')">
                    <div class="action-icon">🔄</div>
                    <div class="action-title">Fund Transfer</div>
                    <div class="action-desc">Transfer between accounts</div>
                </div>
                <div class="action-card warning" onclick="navigateTo('statements')">
                    <div class="action-icon">📊</div>
                    <div class="action-title">View Statements</div>
                    <div class="action-desc">Download account statements</div>
                </div>
            </div>
        </div>

        <!-- Recent Transactions -->
        <div class="recent-transactions animated" style="animation-delay: 0.5s">
            <h2 class="section-title">
                <span>📋</span>
                Recent Transactions
            </h2>
            <div class="transaction-list">
                <div class="transaction-item">
                    <div class="transaction-info">
                        <div class="transaction-desc">Online Transfer to Priya Sharma</div>
                        <div class="transaction-date">Today, 2:30 PM</div>
                    </div>
                    <div class="transaction-amount debit">-₹15,000.00</div>
                </div>
                <div class="transaction-item">
                    <div class="transaction-info">
                        <div class="transaction-desc">Salary Credit - ABC Corp</div>
                        <div class="transaction-date">Yesterday, 9:15 AM</div>
                    </div>
                    <div class="transaction-amount credit">+₹85,000.00</div>
                </div>
                <div class="transaction-item">
                    <div class="transaction-info">
                        <div class="transaction-desc">ATM Withdrawal - MG Road</div>
                        <div class="transaction-date">Aug 8, 6:45 PM</div>
                    </div>
                    <div class="transaction-amount debit">-₹5,000.00</div>
                </div>
                <div class="transaction-item">
                    <div class="transaction-info">
                        <div class="transaction-desc">Cheque Deposit - Ref #CH12345</div>
                        <div class="transaction-date">Aug 7, 11:20 AM</div>
                    </div>
                    <div class="transaction-amount credit">+₹25,500.00</div>
                </div>
            </div>
        </div>
    </main>
</div>
---------------------------------------------------------------------------------------------------------------
