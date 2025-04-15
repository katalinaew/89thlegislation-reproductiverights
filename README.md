# 89thlegislation-reproductiverights
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Track the latest reproductive rights legislation in Texas. Stay informed about bill status, sponsors, and upcoming hearings.">
    <title>Texas Reproductive Rights Bill Tracker</title>
    <style>
        :root {
            --primary-color: #19436b;
            --secondary-color: #e63946;
            --light-color: #f9f9f9;
            --dark-color: #333;
            --border-color: #ddd;
            --shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--dark-color);
            background-color: var(--light-color);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 20px 0;
            box-shadow: var(--shadow);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo h1 {
            font-size: 1.8rem;
        }
        
        .nav-links {
            display: flex;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            margin-left: 20px;
            padding: 5px 10px;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        
        .nav-links a:hover {
            background-color: rgba(255,255,255,0.1);
        }
        
        .intro {
            margin: 20px 0;
            padding: 30px;
            background-color: white;
            border-radius: 8px;
            box-shadow: var(--shadow);
        }
        
        .search-filter {
            margin: 20px 0;
            padding: 20px;
            background-color: white;
            border-radius: 8px;
            box-shadow: var(--shadow);
        }
        
        .search-container {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .search-container input {
            flex: 1;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }
        
        .search-container button {
            padding: 10px 15px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .search-container button:hover {
            background-color: #0f2b47;
        }
        
        .filter-options {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .filter-group {
            flex: 1;
            min-width: 200px;
        }
        
        .filter-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        
        .filter-group select {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }
        
        .tracker-container {
            background-color: white;
            border-radius: 8px;
            padding: 25px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .bill-categories {
            display: flex;
            gap: 10px;
            margin: 15px 0;
            flex-wrap: wrap;
        }
        
        .category-btn {
            padding: 8px 16px;
            background-color: #f0f0f0;
            border: 1px solid var(--border-color);
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .category-btn:hover, .category-btn.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        .subscription-box {
            background-color: #f8f9fa;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 20px;
            margin: 30px 0;
        }
        
        .subscription-box h3 {
            margin-bottom: 15px;
            color: var(--primary-color);
        }
        
        .email-form {
            display: flex;
            gap: 10px;
        }
        
        .email-form input {
            flex: 1;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }
        
        .email-form button {
            padding: 10px 20px;
            background-color: var(--secondary-color);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .email-form button:hover {
            background-color: #c1292e;
        }
        
        footer {
            text-align: center;
            padding: 25px;
            margin-top: 30px;
            background-color: #f1f1f1;
            border-top: 1px solid var(--border-color);
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }
        
        .footer-links a {
            color: var(--primary-color);
            text-decoration: none;
            margin-right: 15px;
        }
        
        .footer-links a:hover {
            text-decoration: underline;
        }
        
        /* Accessibility improvements */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--primary-color);
            color: white;
            padding: 8px;
            z-index: 100;
            transition: top 0.3s;
        }
        
        .skip-link:focus {
            top: 0;
        }
        
        /* Mobile responsiveness */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .nav-links {
                margin-top: 15px;
            }
            
            .search-container, .email-form {
                flex-direction: column;
            }
            
            .footer-content {
                flex-direction: column;
                text-align: center;
            }
            
            .footer-links {
                margin-top: 15px;
            }
        }

        /* Loading indicator */
        .loader {
            border: 5px solid #f3f3f3;
            border-top: 5px solid var(--primary-color);
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 2s linear infinite;
            margin: 20px auto;
            display: none;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Widget customization */
        #BT50Widget {
            margin-top: 20px;
            min-height: 500px;
        }
    </style>
</head>
<body>
    <a href="#main-content" class="skip-link">Skip to main content</a>
    
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <h1>Texas Reproductive Rights Bill Tracker</h1>
                </div>
                <nav class="nav-links">
                    <a href="#" aria-current="page">Home</a>
                    <a href="#">About</a>
                    <a href="#">Resources</a>
                    <a href="#">Contact</a>
                </nav>
            </div>
        </div>
    </header>

    <div class="container" id="main-content">
        <section class="intro">
            <h2>Texas Legislative Session</h2>
            <p>Track the latest bills related to reproductive rights in the Texas legislature. Our tracker provides up-to-date information on bill status, sponsors, and progress through the legislative process.</p>
            <p>Click on any bill to see more details including full text, voting history, and scheduled hearings. Subscribe to email updates to stay informed about changes to bills you're following.</p>
        </section>

        <section class="search-filter">
            <h2>Search and Filter</h2>
            <div class="search-container">
                <input type="text" id="bill-search" placeholder="Search by bill number, keyword, or sponsor" aria-label="Search bills">
                <button id="search-btn">Search</button>
            </div>
            <div class="filter-options">
                <div class="filter-group">
                    <label for="status-filter">Bill Status</label>
                    <select id="status-filter">
                        <option value="all">All Statuses</option>
                        <option value="introduced">Introduced</option>
                        <option value="in-committee">In Committee</option>
                        <option value="passed-house">Passed House</option>
                        <option value="passed-senate">Passed Senate</option>
                        <option value="to-governor">To Governor</option>
                        <option value="enacted">Enacted</option>
                        <option value="vetoed">Vetoed</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label for="chamber-filter">Chamber</label>
                    <select id="chamber-filter">
                        <option value="all">All Chambers</option>
                        <option value="house">House</option>
                        <option value="senate">Senate</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label for="date-filter">Last Action</label>
                    <select id="date-filter">
                        <option value="all">Any Time</option>
                        <option value="week">Past Week</option>
                        <option value="month">Past Month</option>
                        <option value="quarter">Past 3 Months</option>
                    </select>
                </div>
            </div>
        </section>

        <div class="bill-categories">
            <button class="category-btn active">All Bills</button>
            <button class="category-btn">Abortion Access</button>
            <button class="category-btn">Contraception</button>
            <button class="category-btn">Maternal Health</button>
            <button class="category-btn">Sex Education</button>
        </div>

        <section class="tracker-container">
            <h2>Current Bills</h2>
            <div class="loader" id="bills-loader"></div>
            <script src="https://www.billtrack50.com/js/bt50.widget.bill.min.js" type="text/javascript"></script>
            <script type="text/javascript">
                document.addEventListener('DOMContentLoaded', function() {
                    // Show loader
                    document.getElementById('bills-loader').style.display = 'block';
                    
                    // Initialize BillTrack50 widget
                    BT50.Widget({
                        billSheet: '280e57d3-8afd-455e-a48e-5d484562b71a',
                        title: 'Reproductive Rights Legislation',
                        stateFilter: '',
                        rows: 100,
                        tForeground: '#f4f4f4',
                        tBackground: '#19436b',
                        borderColor: '#dddddd',
                        showPosition: true,
                        height: '600px',
                        width: '100%',
                        sortBy: '0',
                        sortDir: 'desc',
                        onLoad: function() {
                            // Hide loader when content is loaded
                            document.getElementById('bills-loader').style.display = 'none';
                        }
                    });
                    
                    // Add event listeners for search and filters
                    document.getElementById('search-btn').addEventListener('click', function() {
                        // Implement search functionality (would require custom integration with BillTrack50 API)
                        alert('Search functionality would be implemented with the BillTrack50 API');
                    });
                    
                    // Category button functionality
                    const categoryButtons = document.querySelectorAll('.category-btn');
                    categoryButtons.forEach(button => {
                        button.addEventListener('click', function() {
                            categoryButtons.forEach(btn => btn.classList.remove('active'));
                            this.classList.add('active');
                            // Would filter content based on category
                        });
                    });
                });
            </script>
            <div id="BT50Widget"></div>
        </section>

        <section class="subscription-box">
            <h3>Stay Informed</h3>
            <p>Subscribe to receive email alerts about changes to reproductive rights legislation in Texas.</p>
            <form class="email-form">
                <input type="email" placeholder="Your email address" aria-label="Email for updates" required>
                <button type="submit">Subscribe</button>
            </form>
        </section>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="copyright">
                    <p>© 2025 Texas Reproductive Rights Bill Tracker | Data provided by BillTrack50</p>
                    <p>Last updated: April 14, 2025</p>
                </div>
                <div class="footer-links">
                    <a href="#">Privacy Policy</a>
                    <a href="#">Terms of Use</a>
                    <a href="#">Accessibility</a>
                    <a href="#">Contact Us</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Additional JavaScript for enhanced functionality
        document.addEventListener('DOMContentLoaded', function() {
            // Example of form submission handling
            const emailForm = document.querySelector('.email-form');
            emailForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const email = this.querySelector('input[type="email"]').value;
                alert(`Thank you! ${email} has been subscribed to updates.`);
                this.reset();
                // In a real implementation, you would send this to your backend
            });
            
            // For demonstration purposes - filter functionality would be implemented 
            // with proper integration to the BillTrack50 API or your own database
            const statusFilter = document.getElementById('status-filter');
            const chamberFilter = document.getElementById('chamber-filter');
            const dateFilter = document.getElementById('date-filter');
            
            [statusFilter, chamberFilter, dateFilter].forEach(filter => {
                filter.addEventListener('change', function() {
                    console.log(`Filter changed: ${this.id} = ${this.value}`);
                    // Would update the bill display based on selected filters
                });
            });
        });
    </script>
</body>
</html>
