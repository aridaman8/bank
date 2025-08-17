<p>admin-login works!</p>
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
    </div>
</header>
<form (ngSubmit)="getAdmin()">
    <div>
        <label for="username">Enter your username</label>
        <input type="text" name="username" id="username" [(ngModel)]="adminDTO.username">
    </div>
    <div *ngIf="hasValidationError('username')" [hidden]="exceptionVisible">
        {{getValidationErrorMessage('username')}}
    </div>
    <br>
    <div>
        <label for="password">Enter Your password</label>
        <input type="password" name="password" id="password" [(ngModel)]="adminDTO.password">
    </div>
    <div>
        <div *ngIf="hasValidationError('password')" [hidden]="exceptionVisible">
            {{getValidationErrorMessage('password')}}
        </div>
    </div>

    {{showResponseError()}}
    <br>
    
    <button type="submit" value="Submit">Submit</button>
</form>

-----------------------------------------------------------------
<p>get-cheque-at-admin works!</p>
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
    </div>
</header>
<table class="get-cheque-at-admin" [hidden]="isVisible">
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
        <td>{{cheque.amount}}</td>

        <td><button
                (click)="getDetailedChequeInfo(createChequeDTO(cheque.chequeNo, cheque.customerAccountNo, cheque.payeeAccountNo))">Take
                Action</button></td>
    </tr>
</table>
<div [hidden]="!isVisible">
    <h1>Cheque Detailed Info</h1>
    <table border="1px solid black">
        <tr>
            <th>Cheque No</th>
            <td>{{extendedChequeDetailDTO.chequeNo}}</td>
        </tr>
        <tr>
            <th>Issuer Name</th>
            <td>{{extendedChequeDetailDTO.issuerName}}</td>
        </tr>
        <tr>
            <th>Issuer Account No</th>
            <td>{{extendedChequeDetailDTO.customerAccountNo}}</td>
        </tr>
        <tr>
            <th>Issuer Account Type</th>
            <td>{{extendedChequeDetailDTO.issuerAccountType}}</td>
        </tr>
        <tr>
            <th>Amount</th>
            <td>{{extendedChequeDetailDTO.chequeAmount}}</td>
        </tr>
        <tr>
            <th>Account Balance</th>
            <td>{{extendedChequeDetailDTO.issuerBalance}}</td>
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving'">
            <th>Saving Minimum Balance</th>{{extendedChequeDetailDTO.savingMinBalance}}
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
            <th>Overdraft Balance</th>
            <td>{{extendedChequeDetailDTO.overDraftBalance}}</td>
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
            <th>Overdraft Limit</th>
            <td>{{extendedChequeDetailDTO.overDraftLimit}}</td>
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'">
            <th>Overdraft Used</th>
            <td>{{extendedChequeDetailDTO.overDraftLimit - extendedChequeDetailDTO.overDraftBalance}}</td>
        </tr>
        

    </table>

    <br>
    <br>

    <table border="1px solid black">
        <tr><th>Payee Name</th><td>{{extendedChequeDetailDTO.payeeName}}</td></tr>
        <tr><th>Payee Account No</th><td>{{extendedChequeDetailDTO.payeeAccountNo}}</td></tr>
        <tr><th>Payee Account Type</th><td>{{extendedChequeDetailDTO.payeeAccountType}}</td></tr>
        <tr><th>Payee Balance</th><td>{{extendedChequeDetailDTO.payeeBalance}}</td></tr>
        <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Saving'"><th>Minimum Balance</th><td>{{extendedChequeDetailDTO.savingMinBalance}}</td></tr>
        <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
            <th>Overdraft Balance</th>
            <td>{{extendedChequeDetailDTO.payeeOverdraftBalance}}</td>
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
            <th>Overdraft Limit</th>
            <td>{{extendedChequeDetailDTO.payeeOverdraftLimit}}</td>
            
        </tr>
        <tr *ngIf="extendedChequeDetailDTO.payeeAccountType=='Current'">
            <th>Overdraft Used</th>
            <td>{{extendedChequeDetailDTO.payeeOverdraftLimit - extendedChequeDetailDTO.payeeOverdraftBalance}}</td>
        </tr>
    </table>
    <br>
    <br>

    <table border="1px solid black">
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Saving'"><th>Saving Balance</th><td>{{extendedChequeDetailDTO.issuerBalance}}</td></tr>
        
        <tr *ngIf="extendedChequeDetailDTO.issuerAccountType=='Current'"><th>Total Balance</th><td>{{extendedChequeDetailDTO.issuerBalance +extendedChequeDetailDTO.overDraftBalance}}</td></tr>
        <tr><th>Cheque Amount</th><td>{{extendedChequeDetailDTO.chequeAmount}}</td></tr>
    </table>
    <button (click)="chequeClearance(chequeClearanceOperation(extendedChequeDetailDTO))">Clear Cheque</button>
    <!-- <button>Bounce Cheque</button> -->
</div>

<div [hidden]="transactionVisible">
    <p>Transaction made {{transactionDTO.status}} against Transaction No {{transactionDTO.transactionId}}</p>
</div>

