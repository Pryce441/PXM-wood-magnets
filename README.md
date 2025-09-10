<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PXM² Crafted Wood – Amplify Project</title>
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f9f6f2; color:#333; }
    header { background:#222; color:white; padding:20px; text-align:center; }
    header h1 { margin:0; font-size:2rem; }
    nav { background:#444; padding:10px; text-align:center; }
    nav a { margin: 0 15px; color:white; text-decoration:none; font-weight:bold; }
    nav a:hover { text-decoration:underline; }
    section { padding:20px; max-width:900px; margin:auto; }
    h2 { color:#8b5e3c; }
    .cta { text-align:center; margin-top:30px; }
    .cta button { background:#8b5e3c; color:white; padding:15px 30px; border:none; border-radius:8px; font-size:1.2rem; cursor:pointer; }
    .cta button:hover { background:#a97452; }
    footer { background:#222; color:white; text-align:center; padding:15px; margin-top:40px; }
  </style>
</head>
<body>


<header>
  <h1>PXM² Crafted Wood and clay magnets</h1>
  <p>Amplify Project – Handmade Wooden Items with AFL Spirit</p>
</header>

<nav>
  <a href="index.html">Home</a>
  <a href="products.html">Our Products</a>
  <a href="#preorder">Preorder</a>
</nav>

<section>
  <h2>About Our Business</h2>
  <p>
    Our team’s chosen idea is to design and sell practical handmade wooden items, 
    focusing on phone holders, and small magnets with 
    fun designs like AFL team jersey's.
  </p>
  <p>
    We believe this idea has strong potential because people value handmade, 
    sustainable products. Wooden items look timeless, last longer than 
    mass-produced alternatives, and customers feel more connected to them—especially 
    when their purchase supports a meaningful social cause.
  </p>
  <p>
    By linking our products to the cause we are amplifying, we add emotional value 
    that encourages people to support us.
  </p>

<section>
  <h2>About Saltbush</h2>
  <p>
    Saltbush offers a sanctuary of respite accommodation and restorative experiences in nature. 
    They support individuals and families facing hardship, providing a space to rest, recharge, 
    and regain the strength needed to navigate life’s challenges.
  </p>
  <p>
    Saltbush, Balnarring Beach maintains low rates for guests to ensure that people with low incomes 
    can access their services. They rely on financial support to maintain these services.
  </p>
  <p>
    Selling our products through PXM² Crafted Wood helps raise money for Saltbush. The funds raised 
    will help maintain and improve their service, accommodation, and site for people who visit it. 
    In addition, Saltbush works with community service organisations to support those in need.
  </p>
</section>

</body>
</html>

<section id="preorder" class="cta">
  <h2>Preorder Your Handmade Item</h2>
  <p>Choose your product, quantity, and AFL team (if selecting magnets). Pricing updates automatically.</p>

  <form id="preorderForm" action="mailto:pryce@e-skips.com" method="post" enctype="text/plain">
    <!-- Customer Name -->
    <label for="name">Your Name:</label><br>
    <input type="text" id="name" name="Name" required><br><br>

    <!-- Email -->
    <label for="email">Your Email:</label><br>
    <input type="email" id="email" name="Email" required><br><br>

    <!-- Product Selection -->
    <label for="product">Select Product:</label><br>
    <select id="product" name="Product" required onchange="showOptions()">
      <option value="">--Choose a Product--</option>
      <option value="Phone Holder">Phone Holder ($10 each)</option>
      <option value="Magnets">AFL Magnets ($3.50 each)</option>
    </select><br><br>

    <!-- Quantity -->
    <div id="quantityDiv" style="display:none;">
      <label for="quantity">Quantity:</label><br>
      <input type="number" id="quantity" name="Quantity" min="1" value="1" onchange="updatePrice()"><br><br>
    </div>

    <!-- AFL Team Selection -->
    <div id="teamDiv" style="display:none;">
      <label for="team">Select AFL Team:</label><br>
      <select id="team" name="AFL Team">
        <option value="">--Choose a Team--</option>
        <option value="Adelaide Crows">Adelaide Crows</option>
        <option value="Brisbane Lions">Brisbane Lions</option>
        <option value="Carlton Blues">Carlton Blues</option>
        <option value="Collingwood Magpies">Collingwood Magpies</option>
        <option value="Essendon Bombers">Essendon Bombers</option>
        <option value="Fremantle Dockers">Fremantle Dockers</option>
        <option value="Geelong Cats">Geelong Cats</option>
        <option value="Gold Coast Suns">Gold Coast Suns</option>
        <option value="GWS Giants">GWS Giants</option>
        <option value="Hawthorn Hawks">Hawthorn Hawks</option>
        <option value="Melbourne Demons">Melbourne Demons</option>
        <option value="North Melbourne Kangaroos">North Melbourne Kangaroos</option>
        <option value="Port Adelaide Power">Port Adelaide Power</option>
        <option value="Richmond Tigers">Richmond Tigers</option>
        <option value="St Kilda Saints">St Kilda Saints</option>
        <option value="Sydney Swans">Sydney Swans</option>
        <option value="West Coast Eagles">West Coast Eagles</option>
        <option value="Western Bulldogs">Western Bulldogs</option>
      </select><br><br>
    </div>

    <!-- Total Price Display -->
    <p><strong>Total Price: $<span id="totalPrice">0.00</span></strong></p>

    <label for="notes">Additional Notes:</label><br>
    <textarea id="notes" name="Notes" rows="3" placeholder="Any custom requests..."></textarea><br><br>

    <input type="submit" value="Send Preorder" style="background:#8b5e3c;color:white;padding:10px 20px;border:none;border-radius:5px;cursor:pointer;">
  </form>
</section>

<script>
function showOptions() {
  const product = document.getElementById('product').value;
  const quantityDiv = document.getElementById('quantityDiv');
  const teamDiv = document.getElementById('teamDiv');

  if (product) {
    quantityDiv.style.display = "block";
  } else {
    quantityDiv.style.display = "none";
  }

  if (product === "Magnets") {
    teamDiv.style.display = "block";
  } else {
    teamDiv.style.display = "none";
  }

  updatePrice();
}

function updatePrice() {
  const product = document.getElementById('product').value;
  const quantity = parseInt(document.getElementById('quantity').value) || 0;
  let price = 0;

  if (product === "Phone Holder") price = 10 * quantity;
  if (product === "Magnets") price = 3.5 * quantity;

  // Bundle: 1 phone holder + 3 magnets = $15
  const phoneQty = product === "Phone Holder" ? quantity : 0;
  const magnetQty = product === "Magnets" ? quantity : 0;

  if (phoneQty === 1 && magnetQty === 3) price = 15;

  document.getElementById('totalPrice').innerText = price.toFixed(2);
}
</script>

<script>
  function showTeams(product) {
    const teamDiv = document.getElementById('teamDiv');
    if(product === "Magnets") {
      teamDiv.style.display = "block";
    } else {
      teamDiv.style.display = "none";
    }
  }
</script>


<footer>
  <p>&copy; 2025 PXM² Crafted Wood | Amplify Project</p>
</footer>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Our Products – PXM² Crafted Wood</title>
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f9f6f2; color:#333; }
    header { background:#222; color:white; padding:20px; text-align:center; }
    nav { background:#444; padding:10px; text-align:center; }
    nav a { margin: 0 15px; color:white; text-decoration:none; font-weight:bold; }
    nav a:hover { text-decoration:underline; }
    section { padding:20px; max-width:900px; margin:auto; }
    h2 { color:#8b5e3c; }
    .product { background:white; padding:20px; margin-bottom:20px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.1); }
    .product img { max-width:100%; border-radius:10px; margin-bottom:10px; }
    footer { background:#222; color:white; text-align:center; padding:15px; margin-top:40px; }
  </style>
</head>
<body>

<header>
  <h1>Our Products</h1>
  <p>Handmade Wooden Creations – Practical, Stylish, and Unique</p>
</header>

<nav>
  <a href="index.html">Home</a>
  <a href="products.html">Our Products</a>
</nav>

<section>
  <div class="product">
    <h2>Wooden Phone Holder (Preorder)</h2>
    <img src=/Users/108032/Desktop/download.jpg> 
    <p>A practical stand for your phone. Preorders open now!</p>
  </div>

  <div class="product">
    <h2>AFL Team Logo Magnets</h2>
    <img Users/108032/Desktop/web edit copy.txt> 
    <p>Small polymer Clay magnets with fun AFL team designs – collect them all!</p>
  </div>
</section>

