import React, { useState, useEffect } from 'react';
import { ShoppingCart, ArrowLeft, Trash2, X, Check } from 'lucide-react';

// --- MOCK PRODUCT DATA ---
const PRODUCTS = [
  { id: 1, name: "Silk Crepe Blouse", price: 145.00, description: "A luxurious silk crepe blouse featuring delicate button detailing and a relaxed silhouette. Perfect for transitioning seamlessly from day to evening." },
  { id: 2, name: "Tailored Wide-Leg Trousers", price: 180.00, description: "High-waisted trousers tailored from premium wool-blend fabric. Features a flawless drape and subtle front pleats for an elegant stride." },
  { id: 3, name: "Cashmere Wrap Coat", price: 395.00, description: "An elegant wrap coat spun from pure, soft cashmere. Features a matching self-tie belt and oversized lapels for timeless sophistication." },
  { id: 4, name: "Leather Crossbody Bag", price: 210.00, description: "Minimalist structured bag crafted from genuine Italian leather. Includes polished gold-tone hardware and an adjustable strap." },
  { id: 5, name: "Linen Midi Dress", price: 165.00, description: "Breathable linen dress perfect for warm, sun-drenched afternoons. Features a subtle V-neckline and a flowing, tiered skirt." },
  { id: 6, name: "Gold Vermeil Hoop Earrings", price: 85.00, description: "Classic, lightweight hoops plated in thick 18k gold vermeil over sterling silver. Designed for comfortable, everyday wear." },
  { id: 7, name: "Suede Pointed Mules", price: 155.00, description: "Effortlessly chic mules with a soft suede finish and a sharp pointed toe. Includes a slight stacked heel for all-day comfort." },
  { id: 8, name: "Ribbed Knit Sweater", price: 125.00, description: "Cozy ribbed knit sweater with a relaxed, slouchy fit. Spun from a plush cotton-wool blend for unmatched softness." }
];

// --- PAYPAL CHECKOUT COMPONENT ---
const PayPalCheckout = ({ total, onPaymentSuccess, onBack }) => {
  const [scriptLoaded, setScriptLoaded] = useState(false);

  useEffect(() => {
    // If PayPal is already loaded on window, proceed
    if (window.paypal) {
      setScriptLoaded(true);
      return;
    }

    // Load the PayPal JS SDK script dynamically
    const script = document.createElement("script");
    const clientId = "AYJ4VDgjnXPXTXGv4v5kHJ_96Z3m47mudvWC4UNBMfBdViaKhNwwUZ-eJZhpx6MjjOPZGYN0IafzfS8f";
    
    script.src = `https://www.paypal.com/sdk/js?client-id=${clientId}&currency=USD`;
    script.async = true;
    script.onload = () => setScriptLoaded(true);
    document.body.appendChild(script);

    return () => {
      // Cleanup script element on unmount to prevent duplicate injections in React
      if (document.body.contains(script)) {
        document.body.removeChild(script);
      }
    };
  }, []);

  useEffect(() => {
    if (scriptLoaded && window.paypal) {
      const container = document.getElementById('paypal-button-container');
      container.innerHTML = ''; // Clear container to prevent duplicate rendering

      window.paypal.Buttons({
        createOrder: (data, actions) => {
          return actions.order.create({
            purchase_units: [{
              amount: {
                value: total.toFixed(2)
              }
            }]
          });
        },
        onApprove: (data, actions) => {
          return actions.order.capture().then(details => {
            onPaymentSuccess(details.payer.name.given_name);
          });
        },
        onError: (err) => {
          console.error("PayPal Checkout Error:", err);
        }
      }).render('#paypal-button-container');
    }
  }, [scriptLoaded, total, onPaymentSuccess]);

  return (
    <div className="max-w-xl mx-auto py-12 px-4 animate-fade-in">
      <h2 className="text-3xl font-serif uppercase tracking-widest text-center mb-10 text-gray-900">Secure Checkout</h2>
      
      <div className="bg-gray-50 p-8 rounded-sm mb-8 border border-gray-100 shadow-sm">
        <div className="flex justify-between mb-6 text-lg text-gray-800">
          <span className="font-light tracking-wide">Total Amount</span>
          <span className="font-semibold">${total.toFixed(2)} USD</span>
        </div>
        <div className="w-full h-[1px] bg-gray-200 mb-8"></div>
        
        <div id="paypal-button-container" className="min-h-[150px] flex items-center justify-center">
          {!scriptLoaded && (
            <p className="text-gray-400 font-light tracking-widest uppercase text-sm animate-pulse">
              Loading Secure Payment Gateway...
            </p>
          )}
        </div>
      </div>

      <div className="text-center">
        <button 
          onClick={onBack}
          className="text-sm tracking-widest uppercase text-gray-500 hover:text-black transition-colors duration-300 border-b border-transparent hover:border-black pb-1"
        >
          Cancel & Return to Cart
        </button>
      </div>
    </div>
  );
};

// --- MAIN APPLICATION ---
export default function App() {
  const [view, setView] = useState('home'); // 'home', 'product', 'cart', 'checkout'
  const [selectedProduct, setSelectedProduct] = useState(null);
  const [cart, setCart] = useState([]);
  const [toast, setToast] = useState(null);
  const [modal, setModal] = useState(null);

  // Helper to show brief toast notification
  const showToast = (message) => {
    setToast(message);
    setTimeout(() => setToast(null), 3000);
  };

  const handleProductClick = (product) => {
    setSelectedProduct(product);
    setView('product');
    window.scrollTo(0, 0);
  };

  const addToCart = (product, e = null) => {
    if (e) e.stopPropagation();
    
    setCart(prev => {
      const existing = prev.find(item => item.id === product.id);
      if (existing) {
        return prev.map(item =>
          item.id === product.id ? { ...item, quantity: item.quantity + 1 } : item
        );
      }
      return [...prev, { ...product, quantity: 1 }];
    });
    showToast(`Added ${product.name} to your cart.`);
  };

  const removeFromCart = (productId) => {
    setCart(prev => prev.filter(item => item.id !== productId));
  };

  const handlePaymentSuccess = (buyerName) => {
    setCart([]);
    setView('home');
    setModal(`Thank you for your elegant purchase, ${buyerName}. Your order from Marina & Elévia has been successfully confirmed.`);
    window.scrollTo(0, 0);
  };

  const cartItemCount = cart.reduce((sum, item) => sum + item.quantity, 0);
  const cartTotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

  return (
    <div className="min-h-screen bg-white text-gray-900 font-sans selection:bg-gray-200">
      
      {/* HEADER */}
      <header className="sticky top-0 bg-white/90 backdrop-blur-md border-b border-gray-100 z-40">
        <div className="max-w-6xl mx-auto px-4 h-24 flex items-center justify-between">
          <div className="w-12"></div> {/* Spacer for perfect centering */}
          
          <h1 
            className="text-2xl md:text-3xl font-serif tracking-widest uppercase cursor-pointer text-center flex-1 hover:opacity-80 transition-opacity"
            onClick={() => setView('home')}
          >
            Marina & Elévia
          </h1>
          
          <button 
            className="w-12 flex justify-end relative text-gray-800 hover:text-black transition-colors"
            onClick={() => { setView('cart'); window.scrollTo(0,0); }}
          >
            <ShoppingCart strokeWidth={1.5} size={26} />
            {cartItemCount > 0 && (
              <span className="absolute -top-1 -right-2 bg-black text-white text-[10px] font-bold w-[18px] h-[18px] flex items-center justify-center rounded-full">
                {cartItemCount}
              </span>
            )}
          </button>
        </div>
      </header>

      {/* MAIN CONTENT AREA */}
      <main className="pb-24">
        
        {/* HOME VIEW: Product Grid */}
        {view === 'home' && (
          <div className="max-w-5xl mx-auto px-4 py-12">
            <div className="grid grid-cols-2 gap-x-6 gap-y-16 md:gap-x-12">
              {PRODUCTS.map(product => (
                <div key={product.id} className="group cursor-pointer flex flex-col" onClick={() => handleProductClick(product)}>
                  
                  {/* Blank Image Placeholder */}
                  <div className="aspect-[4/5] bg-[#F7F7F7] w-full mb-6 overflow-hidden flex items-center justify-center text-gray-300 transition-colors duration-500 group-hover:bg-[#EFEFEF]">
                    <span className="opacity-0 group-hover:opacity-100 transition-opacity duration-300 font-light tracking-widest text-xs uppercase text-gray-500">
                      View Details
                    </span>
                  </div>
                  
                  <div className="flex flex-col items-center text-center flex-1">
                    <h3 className="text-sm md:text-base tracking-wider uppercase text-gray-900 mb-2 font-medium">
                      {product.name}
                    </h3>
                    <p className="text-gray-500 text-sm mb-6 font-light">
                      ${product.price.toFixed(2)}
                    </p>
                    
                    <button 
                      onClick={(e) => addToCart(product, e)}
                      className="mt-auto w-full uppercase tracking-widest text-xs font-semibold py-3 border border-gray-300 text-gray-700 hover:bg-black hover:text-white hover:border-black transition-all duration-300"
                    >
                      Add to Cart
                    </button>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* PRODUCT DETAIL VIEW */}
        {view === 'product' && selectedProduct && (
          <div className="max-w-5xl mx-auto px-4 py-12 animate-fade-in">
            <button 
              onClick={() => setView('home')} 
              className="flex items-center text-xs tracking-widest uppercase text-gray-500 hover:text-black mb-12 transition-colors group"
            >
              <ArrowLeft size={16} className="mr-3 group-hover:-translate-x-1 transition-transform" /> 
              Back to Collection
            </button>
            
            <div className="flex flex-col md:flex-row gap-12 lg:gap-24">
              {/* Large Blank Image Placeholder */}
              <div className="flex-1">
                <div className="w-full aspect-[3/4] bg-[#F7F7F7] flex items-center justify-center">
                   <span className="text-gray-400 font-light tracking-widest uppercase text-sm">
                     Product Image
                   </span>
                </div>
              </div>
              
              <div className="flex-1 flex flex-col justify-center py-8">
                <h2 className="text-3xl md:text-4xl font-serif uppercase tracking-widest mb-4 text-gray-900">
                  {selectedProduct.name}
                </h2>
                <p className="text-2xl text-gray-600 mb-8 font-light">
                  ${selectedProduct.price.toFixed(2)}
                </p>
                
                <div className="w-12 h-[1px] bg-black mb-8"></div>
                
                <p className="text-gray-600 leading-relaxed font-light mb-12 text-lg">
                  {selectedProduct.description}
                </p>
                
                <button 
                  onClick={() => addToCart(selectedProduct)}
                  className="bg-black text-white uppercase tracking-widest text-sm font-semibold py-5 px-8 hover:bg-gray-800 transition-colors duration-300 w-full mb-6"
                >
                  Add to Cart
                </button>
                
                <div className="border-t border-gray-100 pt-6 mt-6">
                  <p className="text-xs text-gray-500 tracking-wider uppercase flex justify-between mb-2">
                    <span>Shipping</span> <span>Complimentary</span>
                  </p>
                  <p className="text-xs text-gray-500 tracking-wider uppercase flex justify-between">
                    <span>Returns</span> <span>Within 30 Days</span>
                  </p>
                </div>
              </div>
            </div>
          </div>
        )}

        {/* CART VIEW */}
        {view === 'cart' && (
          <div className="max-w-4xl mx-auto px-4 py-12 animate-fade-in">
            <h2 className="text-3xl font-serif uppercase tracking-widest text-center mb-16">Your Cart</h2>
            
            {cart.length === 0 ? (
              <div className="text-center py-20 bg-gray-50 border border-gray-100">
                <p className="text-gray-500 mb-6 font-light text-lg">Your selected items will appear here.</p>
                <button 
                  onClick={() => setView('home')} 
                  className="text-black uppercase tracking-widest text-sm border-b border-black pb-1 hover:text-gray-600 hover:border-gray-600 transition-colors"
                >
                  Continue Shopping
                </button>
              </div>
            ) : (
              <div>
                <div className="divide-y divide-gray-100 border-t border-b border-gray-100 mb-12">
                  {cart.map((item, idx) => (
                    <div key={idx} className="py-8 flex items-center justify-between">
                      <div className="flex items-center gap-6">
                        <div className="w-20 h-28 bg-[#F7F7F7] flex items-center justify-center shrink-0"></div>
                        <div>
                          <h4 className="font-serif tracking-wider text-lg mb-1">{item.name}</h4>
                          <p className="text-gray-500 text-sm font-light mb-2">${item.price.toFixed(2)} each</p>
                          <p className="text-gray-400 text-xs tracking-widest uppercase">Qty: {item.quantity}</p>
                        </div>
                      </div>
                      <div className="flex flex-col items-end gap-6">
                        <button 
                          onClick={() => removeFromCart(item.id)} 
                          className="text-gray-400 hover:text-black transition-colors"
                          title="Remove item"
                        >
                          <Trash2 size={18} strokeWidth={1.5} />
                        </button>
                        <p className="font-medium text-lg">${(item.price * item.quantity).toFixed(2)}</p>
                      </div>
                    </div>
                  ))}
                </div>
                
                <div className="flex flex-col items-end">
                  <div className="flex justify-between w-full md:w-1/2 mb-2 text-gray-500 text-sm">
                    <span className="uppercase tracking-widest">Subtotal</span>
                    <span>${cartTotal.toFixed(2)}</span>
                  </div>
                  <div className="flex justify-between w-full md:w-1/2 mb-8 text-gray-900 text-xl font-serif">
                    <span className="uppercase tracking-widest">Estimated Total</span>
                    <span>${cartTotal.toFixed(2)}</span>
                  </div>
                  <p className="text-xs text-gray-400 mb-8 tracking-widest uppercase text-right w-full">
                    Taxes and shipping calculated at checkout
                  </p>
                  
                  <button 
                    onClick={() => { setView('checkout'); window.scrollTo(0,0); }}
                    className="bg-black text-white uppercase tracking-widest text-sm font-semibold py-5 px-12 hover:bg-gray-800 transition-colors duration-300 w-full md:w-auto"
                  >
                    Proceed to Checkout
                  </button>
                </div>
              </div>
            )}
          </div>
        )}

        {/* CHECKOUT VIEW */}
        {view === 'checkout' && (
          <PayPalCheckout 
            total={cartTotal} 
            onPaymentSuccess={handlePaymentSuccess} 
            onBack={() => setView('cart')} 
          />
        )}
      </main>

      {/* TOAST NOTIFICATION */}
      {toast && (
        <div className="fixed bottom-6 right-6 bg-black text-white px-6 py-4 shadow-xl z-50 flex items-center gap-3 animate-fade-in">
          <Check size={18} />
          <span className="font-light tracking-wide text-sm">{toast}</span>
        </div>
      )}

      {/* SUCCESS MODAL UI */}
      {modal && (
        <div className="fixed inset-0 bg-white/80 backdrop-blur-sm flex items-center justify-center z-50 p-4 animate-fade-in">
          <div className="bg-white p-10 max-w-md w-full border border-gray-100 shadow-2xl text-center relative">
            <button 
              onClick={() => setModal(null)} 
              className="absolute top-4 right-4 text-gray-400 hover:text-black transition-colors"
            >
              <X size={20} strokeWidth={1.5} />
            </button>
            <div className="w-16 h-16 bg-black text-white rounded-full flex items-center justify-center mx-auto mb-6">
              <Check size={32} strokeWidth={2} />
            </div>
            <h3 className="text-2xl font-serif tracking-widest uppercase mb-4 text-gray-900">Order Confirmed</h3>
            <p className="text-gray-600 mb-8 font-light leading-relaxed">{modal}</p>
            <button 
              onClick={() => setModal(null)} 
              className="bg-black text-white uppercase tracking-widest text-xs font-semibold py-4 w-full hover:bg-gray-800 transition-colors"
            >
              Continue Shopping
            </button>
          </div>
        </div>
      )}
      
      <style dangerouslySetInnerHTML={{__html: `
        @keyframes fadeIn {
          from { opacity: 0; transform: translateY(10px); }
          to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
          animation: fadeIn 0.4s ease-out forwards;
        }
      `}} />
    </div>
  );
}
