import React from "react";
import { BrowserRouter as Router, Routes, Route, useParams } from "react-router-dom";

function Navbar() {
  return (
    <nav className="bg-black border-b border-gray-800 px-6 py-4 flex justify-between items-center text-white">
      <div className="text-2xl font-bold text-yellow-400">DN</div>
      <ul className="flex gap-6 text-sm">
        <li><a href="/" className="hover:text-yellow-400 transition">Home</a></li>
        <li><a href="/shop" className="hover:text-yellow-400 transition">Shop</a></li>
        <li><a href="/about" className="hover:text-yellow-400 transition">About</a></li>
        <li><a href="/contact" className="hover:text-yellow-400 transition">Contact</a></li>
      </ul>
    </nav>
  );
}

function Footer() {
  return (
    <footer className="bg-black border-t border-gray-800 text-center py-6 text-sm text-gray-400">
      &copy; {new Date().getFullYear()} David's Shoe Collection. All rights reserved.
    </footer>
  );
}

function HeroSection() {
  return (
    <section className="bg-black text-white text-center py-20 px-6">
      <h1 className="text-4xl md:text-6xl font-bold text-yellow-400 mb-4">Styling Your Looks</h1>
      <p className="text-lg md:text-xl text-gray-300 mb-8">Step into elegance with premium footwear crafted for bold lifestyles.</p>
      <a href="/shop" className="inline-block bg-yellow-400 text-black px-8 py-3 rounded-full font-semibold hover:bg-yellow-300 transition">Shop Now</a>
    </section>
  );
}

function FeaturedProducts() {
  const products = [
    {
      name: "Brown Leather Slip-On",
      image: "/images/shoe1.jpg",
      price: "Ksh 3,500"
    },
    {
      name: "Black Sports Sneaker",
      image: "/images/shoe2.jpg",
      price: "Ksh 4,200"
    },
    {
      name: "Black Croc Loafer",
      image: "/images/shoe3.jpg",
      price: "Ksh 3,800"
    }
  ];

  return (
    <section className="bg-black text-white py-16 px-6">
      <h2 className="text-3xl font-semibold text-center text-yellow-400 mb-10">Featured Shoes</h2>
      <div className="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
        {products.map((product, idx) => (
          <div key={idx} className="bg-gray-900 rounded-xl p-4 shadow hover:shadow-lg transition">
            <img src={product.image} alt={product.name} className="rounded-lg mb-4 h-64 w-full object-cover" />
            <h3 className="text-xl font-bold text-yellow-300 mb-2">{product.name}</h3>
            <p className="text-white mb-4">{product.price}</p>
            <a href={`/product/${idx + 1}`} className="inline-block bg-yellow-400 text-black px-5 py-2 rounded-full text-sm font-semibold hover:bg-yellow-300">View Details</a>
          </div>
        ))}
      </div>
    </section>
  );
}

function ProductPage() {
  const { id } = useParams();
  const productList = [
    {
      name: "Brown Leather Slip-On",
      image: "/images/shoe1.jpg",
      price: "Ksh 3,500"
    },
    {
      name: "Black Sports Sneaker",
      image: "/images/shoe2.jpg",
      price: "Ksh 4,200"
    },
    {
      name: "Black Croc Loafer",
      image: "/images/shoe3.jpg",
      price: "Ksh 3,800"
    }
  ];

  const product = productList[parseInt(id, 10) - 1];

  if (!product) {
    return <div className="text-white text-center py-20">Product not found.</div>;
  }

  return (
    <section className="bg-black text-white py-16 px-6 max-w-4xl mx-auto">
      <div className="grid md:grid-cols-2 gap-10">
        <img src={product.image} alt={product.name} className="rounded-lg w-full object-cover h-96" />
        <div>
          <h2 className="text-3xl font-bold text-yellow-400 mb-4">{product.name}</h2>
          <p className="text-lg text-white mb-4">{product.price}</p>
          <h3 className="text-lg font-semibold text-yellow-300 mb-2">Payment Instructions:</h3>
          <ul className="text-sm text-gray-300 list-disc pl-5 mb-4">
            <li>Go to M-Pesa &gt; Lipa na M-Pesa &gt; Send Money</li>
            <li>Enter Number: <span className="font-bold text-yellow-400">0707 847789</span></li>
            <li>Amount: <span className="font-bold">{product.price}</span></li>
          </ul>
          <a href={`https://wa.me/254707847789?text=${encodeURIComponent(`Hi David, I've just made a payment for ${product.name}`)}`} target="_blank" rel="noopener noreferrer" className="inline-block bg-green-500 text-white px-5 py-2 rounded-full text-sm font-semibold hover:bg-green-400 mb-4">Confirm via WhatsApp</a>
          <p className="text-yellow-300 font-semibold">Thank you for shopping with David's Shoe Collection.</p>
          <p className="text-sm text-red-500 mt-2 italic">Note: All sales are final. We operate a no return policy.</p>
        </div>
      </div>
    </section>
  );
}

function ShopPage() {
  const products = [
    {
      name: "Brown Leather Slip-On",
      image: "/images/shoe1.jpg",
      price: "Ksh 3,500"
    },
    {
      name: "Black Sports Sneaker",
      image: "/images/shoe2.jpg",
      price: "Ksh 4,200"
    },
    {
      name: "Black Croc Loafer",
      image: "/images/shoe3.jpg",
      price: "Ksh 3,800"
    }
  ];

  return (
    <section className="bg-black text-white py-16 px-6">
      <h1 className="text-3xl font-bold text-center text-yellow-400 mb-10">Shop All Shoes</h1>
      <div className="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
        {products.map((product, idx) => (
          <div key={idx} className="bg-gray-900 rounded-xl p-4 shadow hover:shadow-lg transition">
            <img src={product.image} alt={product.name} className="rounded-lg mb-4 h-64 w-full object-cover" />
            <h3 className="text-xl font-bold text-yellow-300 mb-2">{product.name}</h3>
            <p className="text-white mb-4">{product.price}</p>
            <a href={`/product/${idx + 1}`} className="inline-block bg-yellow-400 text-black px-5 py-2 rounded-full text-sm font-semibold hover:bg-yellow-300">View Details</a>
          </div>
        ))}
      </div>
    </section>
  );
}

function App() {
  return (
    <Router>
      <div className="min-h-screen flex flex-col bg-black text-white font-sans">
        <Navbar />
        <main className="flex-grow">
          <HeroSection />
          <FeaturedProducts />
          <Routes>
            <Route path="/" element={<ShopPage />} />
            <Route path="/shop" element={<ShopPage />} />
            <Route path="/product/:id" element={<ProductPage />} />
          </Routes>
        </main>
        <Footer />
      </div>
    </Router>
  );
}

export default App;
