<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SecureBank - Admin Cheque Management</title>
<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
}

body {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
background: linear-gradient(135deg, #2c3e50 0%, #34495e 50%, #2c3e50 100%);
min-height: 100vh;
display: flex;
flex-direction: column;
color: #2c3e50;
}

/* Header */
header {
background: rgba(0, 0, 0, 0.3);
backdrop-filter: blur(10px);
padding: 1rem 2rem;
box-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
position: sticky;
top: 0;
z-index: 100;
}

.header-content {
max-width: 1400px;
margin: 0 auto;
display: flex;
justify-content: space-between;
align-items: center;
}

.logo {
display: flex;
align-items: center;
gap: 10px;
font-size: 1.5rem;
font-weight: bold;
color: white;
}

.logo-icon {
width: 40px;
height: 40px;
background: linear-gradient(45deg, #e74c3c, #c0392b);
border-radius: 8px;
display: flex;
align-items: center;
justify-content: center;
color: white;
font-weight: bold;
}

.nav-links {
display: flex;
list-style: none;
gap: 2rem;
}

.nav-links a {
color: rgba(255, 255, 255, 0.8);
text-decoration: none;
font-weight: 500;
transition: all 0.3s ease;
}

.nav-links a:hover {
color: #e74c3c;
}

.admin-badge {
background: linear-gradient(135deg, #e74c3c, #c0392b);
color: white;
padding: 0.5rem 1rem;
border-radius: 20px;
font-size: 0.8rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 1px;
}

/* Main Content */
main {
flex: 1;
padding: 2rem;
}

/* Page Header */
.page-header {
background: rgba(255, 255, 255, 0.95);
backdrop-filter: blur(10px);
border-radius: 20px;
padding: 2rem;
margin-bottom: 2rem;
box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
text-align: center;
animation: slideUp 0.6s ease-out;
}

.page-title {
display: flex;
align-items: center;
justify-content: center;
gap: 1rem;
margin-bottom: 1rem;
}

.page-title h1 {
color: #2c3e50;
font-size: 2.5rem;
}

.page-title .icon {
font-size: 3rem;
animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
0%, 100% { transform: scale(1); }
50% { transform: scale(1.05); }
}

.page-subtitle {
color: #7f8c8d;
font-size: 1.2rem;
}

/* Cheques Table Section */
.cheques-section {
background: rgba(255, 255, 255, 0.95);
backdrop-filter: blur(10px);
border-radius: 20px;
padding: 2rem;
box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
animation: slideUp 0.6s ease-out 0.1s both;
margin-bottom: 2rem;
}

.section-header {
display: flex;
align-items: center;
justify-content: between;
margin-bottom: 2rem;
}

.section-title {
color: #2c3e50;
font-size: 1.8rem;
display: flex;
align-items: center;
gap: 0.5rem;
}

/* Table Styling */
.get-cheque-at-admin {
width: 100%;
border-collapse: collapse;
background: white;
border-radius: 15px;
overflow: hidden;
box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
margin-top: 1rem;
}

.get-cheque-at-admin th {
background: linear-gradient(135deg, #e74c3c, #c0392b);
color: white;
padding: 1.2rem;
text-align: left;
font-weight: 600;
text-transform: uppercase;
font-size: 0.9rem;
letter-spacing: 0.5px;
}

.get-cheque-at-admin td {
padding: 1.2rem;
border-bottom: 1px solid #ecf0f1;
color: #2c3e50;
font-size: 1rem;
}

.get-cheque-at-admin tr {
transition: all 0.3s ease;
}

.get-cheque-at-admin tr:hover {
background: rgba(231, 76, 60, 0.05);
transform: translateX(5px);
}

.get-cheque-at-admin tr:last-child td {
border-bottom: none;
}

/* Amount styling */
.get-cheque-at-admin td:nth-child(4) {
font-weight: 600;
color: #27ae60;
font-size: 1.1rem;
}

/* Action button styling */
.action-btn {
background: linear-gradient(135deg, #3498db, #2980b9);
color: white;
border: none;
padding: 0.8rem 1.5rem;
border-radius: 10px;
cursor: pointer;
font-size: 0.9rem;
font-weight: 600;
transition: all 0.3s ease;
text-transform: uppercase;
letter-spacing: 0.5px;
}

.action-btn:hover {
transform: translateY(-2px);
box-shadow: 0 8px 20px rgba(52, 152, 219, 0.3);
}

/* Detailed Cheque Info Section */
.cheque-details-section {
background: rgba(255, 255, 255, 0.95);
backdrop-filter: blur(10px);
border-radius: 20px;
padding: 2rem;
box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
animation: slideUp 0.6s ease-out 0.2s both;
}

.details-header {
text-align: center;
margin-bottom: 2rem;
padding-bottom: 1rem;
border-bottom: 2px solid #ecf0f1;
}

.details-header h1 {
color: #2c3e50;
font-size: 2rem;
display: flex;
align-items: center;
justify-content: center;
gap: 0.5rem;
}

/* Details Tables Grid */
.details-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 2rem;
margin-bottom: 2rem;
}

.detail-table {
background: white;
border-radius: 15px;
overflow: hidden;
box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.detail-table h3 {
background: linear-gradient(135deg, #3498db, #2980b9);
color: white;
padding: 1rem;
margin: 0;
font-size: 1.1rem;
text-align: center;
}

.detail-table table {
width: 100%;
border-collapse: collapse;
}

.detail-table th {
background: #ecf0f1;
color: #2c3e50;
padding: 1rem;
text-align: left;
font-weight: 600;
width: 50%;
}

.detail-table td {
padding: 1rem;
border-bottom: 1px solid #ecf0f1;
color: #555;
font-weight: 500;
}

.detail-table tr:last-child td {
border-bottom: none;
}

/* Summary Table */
.summary-table {
background: linear-gradient(135deg, #f8f9fa, #e9ecef);
border-radius: 15px;
overflow: hidden;
margin-bottom: 2rem;
border: 2px solid #3498db;
}

.summary-table h3 {
background: linear-gradient(135deg, #27ae60, #229954);
color: white;
padding: 1rem;
margin: 0;
text-align: center;
font-size: 1.2rem;
}

/* Action Buttons */
.action-buttons {
display: flex;
justify-content: center;
gap: 1rem;
margin-top: 2rem;
}

.btn-approve {
background: linear-gradient(135deg, #27ae60, #229954);
color: white;
border: none;
padding: 1.2rem 2.5rem;
border-radius: 12px;
cursor: pointer;
font-size: 1.1rem;
font-weight: 600;
transition: all 0.3s ease;
text-transform: uppercase;
letter-spacing: 1px;
}

.btn-approve:hover {
transform: translateY(-3px);
box-shadow: 0 10px 25px rgba(39, 174, 96, 0.4);
}

.btn-bounce {
background: linear-gradient(135deg, #e74c3c, #c0392b);
color: white;
border: none;
padding: 1.2rem 2.5rem;
border-radius: 12px;
cursor: pointer;
font-size: 1.1rem;
font-weight: 600;
transition: all 0.3s ease;
text-transform: uppercase;
letter-spacing: 1px;
}

.btn-bounce:hover {
transform: translateY(-3px);
box-shadow: 0 10px 25px rgba(231, 76, 60, 0.4);
}

/* Transaction Status */
.transaction-status {
background: rgba(39, 174, 96, 0.1);
border: 2px solid #27ae60;
border-radius: 15px;
padding: 2rem;
text-align: center;
animation: slideUp 0.6s ease-out;
}

.transaction-status p {
font-size: 1.2rem;
color: #27ae60;
font-weight: 600;
}

/* Empty State */
.empty-state {
text-align: center;
padding: 4rem;
color: #7f8c8d;
}

.empty-state .icon {
font-size: 4rem;
margin-bottom: 1rem;
opacity: 0.5;
}

/* Responsive Design */
@media (max-width: 1024px) {
.details-grid {
grid-template-columns: 1fr;
}
}

@media (max-width: 768px) {
main {
padding: 1rem;
}

.cheques-section,
.cheque-details-section,
.page-header {
padding: 1.5rem;
}

.get-cheque-at-admin th,
.get-cheque-at-admin td {
padding: 0.8rem 0.5rem;
font-size: 0.9rem;
}

.action-buttons {
flex-direction: column;
align-items: center;
}

.btn-approve,
.btn-bounce {
width: 100%;
max-width: 300px;
}

.nav-links {
display: none;
}

.page-title h1 {
font-size: 2rem;
}

.page-title .icon {
font-size: 2.5rem;
}
}

/* Animations */
@keyframes slideUp {
from {
opacity: 0;
transform: translateY(30px);
}
to {
opacity: 1;
transform: translateY(0);
}
}

/* Loading Animation */
.loading {
display: inline-block;
width: 20px;
height: 20px;
border: 2px solid #ffffff;
border-radius: 50%;
border-top-color: transparent;
animation: spin 1s ease-in-out infinite;
margin-right: 10px;
}

@keyframes spin {
to { transform: rotate(360deg); }
}
</style>
</head>
<body>
<p style="display: none;">get-cheque-at-admin works!</p>

<!-- Header -->
<header>
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
        <div class="admin-badge">🔐 Admin Panel</div>
    </div>
</header>

<main>
    <!-- Page Header -->
    <div class="page-header">
        <div class="page-title">
            <span class="icon">📋</span>
            <h1>Cheque Management</h1>
        </div>
        <p class="page-subtitle">Review and process pending cheque transactions</p>
    </div>

    <!-- Cheques Table Section -->
    <div class="cheques-section" [hidden]="isVisible">
        <div class="section-header">
            <h2 class="section-title">
                <span>⏳</span>
                Pending Cheques for Review
            </h2>
        </div>

        <table class="get-cheque-at-admin">
            <tr>
                <th>Cheque No.</th>
                <th>Customer Account No.</th>
                <th>Payee Account No.</th>
                <th>Amount</th>
                <th>Action</th>
            </tr>
            <tr *ngFor="let cheque of cheques">
                <td>{{cheque.chequeNo}}</td>
                <td>{{cheque.customerAccountNo}}</td>
                <td>{{cheque.payeeAccountNo}}</td>
                <td>₹{{cheque.amount}}</td>
                <td>
                    <button class="action-btn"
                            (click)="getDetailedChequeInfo(createChequeDTO(cheque.chequeNo, cheque.customerAccountNo, cheque.payeeAccountNo))">
                        📊 Review Details
                    </button>
                </td>
            </tr>
        </table>

        <!-- Empty State -->
        <div class="empty-state" *ngIf="!cheques || cheques.length === 0">
            <div class="icon">📝</div>
            <h3>No Pending Cheques</h3>
            <p>All cheques have been processed.</p>
        </div>
    </div>

    <!-- Detailed Cheque Info Section -->
    <div class="cheque-details-section" [hidden]="!isVisible">
        <div class="details-header">
            <h1>
                <span>🔍</span>
                Cheque Detailed Information
            </h1>
        </div>

        <!-- Issuer and Payee Information Grid -->
        <div class="details-grid">
            <!-- Issuer Information -->
            <div class="detail-table">
                <h3>💳 Issuer Information</h3>
                <table>
                    <tr>
                        <th>Cheque No</th>
                        <td>{{extendedChequeDetailDTO.chequeNo}}</td>
                    </tr>
                    <tr>
                        <th>Issuer Name</th>
                        <td>{{extendedChequeDetailDTO.issuerName}}</td>
                    </tr>
                    <tr>
                        <th>Account No</th>
                        <td>{{extendedChequeDetailDTO.customerAccountNo}}</td>
                    </tr>
                    <tr>
                        <th>Account Type</th>
                        <td>{{extendedChequeDetailDTO.issuerAccountType}}</td>
                    </tr>
                    <tr>
                        <th>Current Balance</th>
                        <td>₹{{extendedChequeDetailDTO.issuerBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving'">
                        <th>Min Balance Required</th>
                        <td>₹{{extendedChequeDetailDTO.savingMinBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
                        <th>Overdraft Balance</th>
                        <td>₹{{extendedChequeDetailDTO.overDraftBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
                        <th>Overdraft Limit</th>
                        <td>₹{{extendedChequeDetailDTO.overDraftLimit}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
                        <th>Overdraft Used</th>
                        <td>₹{{extendedChequeDetailDTO.overDraftLimit - extendedChequeDetailDTO.overDraftBalance}}</td>
                    </tr>
                </table>
            </div>

            <!-- Payee Information -->
            <div class="detail-table">
                <h3>👤 Payee Information</h3>
                <table>
                    <tr>
                        <th>Payee Name</th>
                        <td>{{extendedChequeDetailDTO.payeeName}}</td>
                    </tr>
                    <tr>
                        <th>Account No</th>
                        <td>{{extendedChequeDetailDTO.payeeAccountNo}}</td>
                    </tr>
                    <tr>
                        <th>Account Type</th>
                        <td>{{extendedChequeDetailDTO.payeeAccountType}}</td>
                    </tr>
                    <tr>
                        <th>Current Balance</th>
                        <td>₹{{extendedChequeDetailDTO.payeeBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Saving'">
                        <th>Min Balance Required</th>
                        <td>₹{{extendedChequeDetailDTO.savingMinBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
                        <th>Overdraft Balance</th>
                        <td>₹{{extendedChequeDetailDTO.payeeOverdraftBalance}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
                        <th>Overdraft Limit</th>
                        <td>₹{{extendedChequeDetailDTO.payeeOverdraftLimit}}</td>
                    </tr>
                    <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
                        <th>Overdraft Used</th>
                        <td>₹{{extendedChequeDetailDTO.payeeOverdraftLimit - extendedChequeDetailDTO.payeeOverdraftBalance}}</td>
                    </tr>
                </table>
            </div>
        </div>

        <!-- Transaction Summary -->
        <div class="summary-table">
            <h3>💰 Transaction Summary</h3>
            <table>
                <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving'">
                    <th>Available Balance</th>
                    <td>₹{{extendedChequeDetailDTO.issuerBalance}}</td>
                </tr>
                <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
                    <th>Total Available Balance</th>
                    <td>₹{{extendedChequeDetailDTO.issuerBalance + extendedChequeDetailDTO.overDraftBalance}}</td>
                </tr>
                <tr>
                    <th>Cheque Amount</th>
                    <td>₹{{extendedChequeDetailDTO.chequeAmount}}</td>
                </tr>
                <tr>
                    <th>Transaction Status</th>
                    <td>
                        <span *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving' && extendedChequeDetailDTO.issuerBalance >= extendedChequeDetailDTO.chequeAmount" 
                              style="color: #27ae60; font-weight: bold;">✅ Sufficient Balance</span>
                        <span *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current' && (extendedChequeDetailDTO.issuerBalance + extendedChequeDetailDTO.overDraftBalance) >= extendedChequeDetailDTO.chequeAmount" 
                              style="color: #27ae60; font-weight: bold;">✅ Sufficient Balance</span>
                        <span *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving' && extendedChequeDetailDTO.issuerBalance < extendedChequeDetailDTO.chequeAmount" 
                              style="color: #e74c3c; font-weight: bold;">❌ Insufficient Balance</span>
                        <span *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current' && (extendedChequeDetailDTO.issuerBalance + extendedChequeDetailDTO.overDraftBalance) < extendedChequeDetailDTO.chequeAmount" 
                              style="color: #e74c3c; font-weight: bold;">❌ Insufficient Balance</span>
                    </td>
                </tr>
            </table>
        </div>

        <!-- Action Buttons -->
        <div class="action-buttons">
            <button class="btn-approve" 
                    (click)="chequeClearance(chequeClearanceOperation(extendedChequeDetailDTO))"
                    [disabled]="(extendedChequeDetailDTO.issuerAccountType=='Saving' && extendedChequeDetailDTO.issuerBalance < extendedChequeDetailDTO.chequeAmount) || 
                               (extendedChequeDetailDTO.issuerAccountType=='Current' && (extendedChequeDetailDTO.issuerBalance + extendedChequeDetailDTO.overDraftBalance) < extendedChequeDetailDTO.chequeAmount)">
                <span class="loading" style="display: none;"></span>
                ✅ Clear Cheque
            </button>
            <button class="btn-bounce">
                ❌ Bounce Cheque
            </button>
        </div>
    </div>

    <!-- Transaction Result -->
    <div class="transaction-status" [hidden]="transactionVisible">
        <p>
            <span *ngIf="transactionDTO.status === 'Success'">✅</span>
            <span *ngIf="transactionDTO.status !== 'Success'">❌</span>
            Transaction {{transactionDTO.status}} - Transaction ID: {{transactionDTO.transactionId}}
        </p>
    </div>
</main>

<script>
// Mock functions for demonstration
function createChequeDTO(chequeNo, customerAccountNo, payeeAccountNo) {
    return {
        chequeNo: chequeNo,
        customerAccountNo: customerAccountNo,
        payeeAccountNo: payeeAccountNo
    };
}

function chequeClearanceOperation(extendedChequeDetailDTO) {
    return {
        // Your clearance operation logic
        chequeNo: extendedChequeDetailDTO.chequeNo,
        amount: extendedChequeDetailDTO.chequeAmount,
        issuerAccount: extendedChequeDetailDTO.customerAccountNo,
        payeeAccount: extendedChequeDetailDTO.payeeAccountNo
    };
}

// Add loading animation for buttons
document.addEventListener('DOMContentLoaded', function() {
    const approveBtn = document.querySelector('.btn-approve');
    const bounceBtn = document.querySelector('.btn-bounce');
    
    if (approveBtn) {
        approveBtn.addEventListener('click', function() {
            const loading = this.querySelector('.loading');
            if (loading) {
                loading.style.display = 'inline-block';
                this.disabled = true;
                
                // Reset after processing (remove in actual implementation)
                setTimeout(() => {
                    loading.style.display = 'none';
                    this.disabled = false;
                }, 3000);
            }
        });
    }
});
</script>
</body>
</html>
