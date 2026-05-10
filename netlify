import React, { useState, useRef, useEffect } from 'react';
import { motion, AnimatePresence, useMotionValue, useSpring } from 'framer-motion';
import { 
  Monitor, Smartphone, X, Check, Calendar, FileText, 
  Activity, LayoutGrid, Zap, ShieldCheck, ChevronRight,
  Users, FileDigit, UploadCloud, ArrowRight, Box, Cpu,
  Droplets, ThermometerSun, MapPin, Search, Plus, CreditCard,
  PhoneCall, Shield, Menu, Star, Wrench, CheckCircle2, Scale, Building2,
  Clock, HeartHandshake, Leaf, Sun, Play, Pause, ChevronLeft,
  Sparkles, Car, Home, Briefcase, LineChart, Stethoscope, HardHat, Camera
} from 'lucide-react';

// ==========================================
// EXPANDED DATA STRUCTURES
// ==========================================

const ARCHITECTURES = [
  { id: 'arc-1', category: 'HVAC', name: 'Arctic Command', tagline: 'Thermal dominance engine.', basePrice: 8500, conversionRate: 14.2, loadTime: 0.8, features: ['Automated Dispatch Sync', 'Seasonal Promo Engine', 'Energy Rebate Calculator', 'Emergency Routing'], color: 'text-blue-500', bg: 'bg-blue-500' },
  { id: 'arc-2', category: 'Plumbing', name: 'Pipeline Command', tagline: 'Fluid operational flow.', basePrice: 7500, conversionRate: 12.8, loadTime: 0.7, features: ['Emergency Leak Protocol', 'Video Inspection Portal', 'Municipal Permit Integration', 'Financing Calculator'], color: 'text-cyan-500', bg: 'bg-cyan-500' },
  { id: 'arc-3', category: 'Electrical', name: 'Voltage Authority', tagline: 'High-current conversions.', basePrice: 7800, conversionRate: 13.5, loadTime: 0.8, features: ['Smart Home Integration', 'Code Compliance Checker', 'EV Charger Quoting', 'Grid-Fail Response'], color: 'text-yellow-400', bg: 'bg-yellow-400' },
  { id: 'arc-4', category: 'Roofing', name: 'Storm Shield', tagline: 'Impenetrable lead capture.', basePrice: 9000, conversionRate: 15.1, loadTime: 0.9, features: ['Drone Mapping Uplink', 'Insurance Claim Generator', 'Material Visualizer', 'Weather-Triggered Promos'], color: 'text-orange-500', bg: 'bg-orange-500' },
  { id: 'arc-5', category: 'Solar', name: 'Photon System', tagline: 'Maximize grid independence.', basePrice: 12500, conversionRate: 16.7, loadTime: 1.1, features: ['Satellite Roof Analysis', 'ROI Simulation Matrix', 'Tax Credit Automator', 'Battery Storage Upsell'], color: 'text-amber-500', bg: 'bg-amber-500' },
  { id: 'arc-6', category: 'Luxury Landscaping', name: 'Eden Protocol', tagline: 'Organic aesthetic mastery.', basePrice: 10500, conversionRate: 11.9, loadTime: 1.0, features: ['3D CAD Walkthroughs', 'Botanical Database', 'Seasonal Maintenance Portal', 'Irrigation Telemetry'], color: 'text-green-500', bg: 'bg-green-500' },
  { id: 'arc-7', category: 'MedSpa', name: 'Radiant Core', tagline: 'Clinical precision UI.', basePrice: 11000, conversionRate: 18.3, loadTime: 0.9, features: ['HIPAA Compliant Intake', 'Before/After Slider', 'Virtual Consult Booking', 'Membership Portal'], color: 'text-pink-500', bg: 'bg-pink-500' },
  { id: 'arc-8', category: 'Legal', name: 'Justice Engine', tagline: 'Authoritative case acquisition.', basePrice: 13500, conversionRate: 9.8, loadTime: 0.8, features: ['Encrypted Vault', 'Conflict Check Matrix', 'Retainer Automation', 'Deposition Scheduler'], color: 'text-slate-400', bg: 'bg-slate-400' },
  { id: 'arc-9', category: 'Cleaning Services', name: 'Pristine Protocol', tagline: 'Spotless conversion funnels.', basePrice: 4500, conversionRate: 19.2, loadTime: 0.6, features: ['Instant Square-Foot Quoting', 'Recurring Subscription Upsell', 'Cleaner Rating System', 'Before/After Gallery'], color: 'text-teal-400', bg: 'bg-teal-400' },
  { id: 'arc-10', category: 'Real Estate', name: 'Broker Blueprint', tagline: 'High-ticket property showcases.', basePrice: 14000, conversionRate: 8.5, loadTime: 1.2, features: ['MLS API Integration', 'Virtual 3D Tours', 'Neighborhood Data Feeds', 'Mortgage Calculator'], color: 'text-indigo-500', bg: 'bg-indigo-500' },
  { id: 'arc-11', category: 'Wealth Management', name: 'Capital Vault', tagline: 'High-net-worth client acquisition.', basePrice: 16500, conversionRate: 7.2, loadTime: 0.9, features: ['Secure Client Portal', 'Market Data Integration', 'Retirement Calculators', 'Encrypted Document Drop'], color: 'text-emerald-500', bg: 'bg-emerald-500' },
  { id: 'arc-12', category: 'Auto Repair', name: 'Velocity Engine', tagline: 'High-octane service bookings.', basePrice: 6500, conversionRate: 14.8, loadTime: 0.7, features: ['License Plate Lookup API', 'Digital Inspection Reports', 'Service Reminder Texts', 'Tire Size Calculator'], color: 'text-red-500', bg: 'bg-red-500' }
];

const APPS = [
  { id: 'app-1', category: 'Field Software', name: 'The Dispatcher', tagline: 'Complete field service operations CRM.', basePrice: 299, recurring: true, conversionRate: '--', loadTime: 0.4, features: ['Live Fleet Tracking', 'Drag-and-Drop Calendar', 'On-Site Invoicing', 'Automated SMS Reminders'], color: 'text-purple-500', bg: 'bg-purple-500', tabs: ['Leads', 'Calendar', 'Invoicing', 'Analytics'] },
  { id: 'app-2', category: 'Clinic Software', name: 'Patient Portal', tagline: 'HIPAA compliant practice management.', basePrice: 399, recurring: true, conversionRate: '--', loadTime: 0.5, features: ['Secure Medical Records', 'Automated Scheduling', 'Telehealth Integration', 'Insurance Verification'], color: 'text-pink-500', bg: 'bg-pink-500', tabs: ['Documents', 'Appointments', 'Messages', 'Records'] },
  { id: 'app-3', category: 'Finance Software', name: 'Client Vault', tagline: 'Bank-grade secure document exchange.', basePrice: 499, recurring: true, conversionRate: '--', loadTime: 0.3, features: ['256-bit Encryption', 'E-Signatures', 'Tax Form Parsing', 'Client Messaging'], color: 'text-emerald-500', bg: 'bg-emerald-500', tabs: ['Vault', 'Signatures', 'Messages', 'Taxes'] },
  { id: 'app-4', category: 'Construction', name: 'Crew Tracker', tagline: 'Jobsite time and material tracking.', basePrice: 199, recurring: true, conversionRate: '--', loadTime: 0.6, features: ['GPS Geofenced Clock-in', 'Material Receipt Scanning', 'Daily Log Generation', 'Weather Delay Alerts'], color: 'text-orange-500', bg: 'bg-orange-500', tabs: ['Map', 'Logs', 'Receipts', 'Alerts'] }
];

const ADDONS = [
  { id: 'add-1', name: 'Custom SEO Copywriting', price: 1000, recurring: false },
  { id: 'add-2', name: 'CRM App Integration', price: 500, recurring: true },
  { id: 'add-3', name: 'Priority 24hr Deployment', price: 2000, recurring: false },
  { id: 'add-4', name: 'White Glove Support', price: 300, recurring: true },
  { id: 'add-5', name: 'Custom Integrations Package', price: 1500, recurring: false }
];

const formatCurrency = (amount) => new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', minimumFractionDigits: 0 }).format(amount);

// ==========================================
// CORE UTILITIES
// ==========================================

const MagneticButton = ({ children, variant = 'primary', onClick, className = '', fullWidth = false }) => {
  const ref = useRef(null);
  const x = useMotionValue(0);
  const y = useMotionValue(0);
  
  const springConfig = { damping: 15, stiffness: 150, mass: 0.1 };
  const springX = useSpring(x, springConfig);
  const springY = useSpring(y, springConfig);

  const handleMouseMove = (e) => {
    if (!ref.current) return;
    const rect = ref.current.getBoundingClientRect();
    const center_x = rect.left + rect.width / 2;
    const center_y = rect.top + rect.height / 2;
    x.set((e.clientX - center_x) * 0.2);
    y.set((e.clientY - center_y) * 0.2);
  };

  const handleMouseLeave = () => {
    x.set(0);
    y.set(0);
  };

  const variants = {
    primary: "bg-white text-black hover:bg-neutral-200 py-3 px-6",
    secondary: "bg-white/5 text-white border border-white/10 hover:bg-white/10 py-3 px-6"
  };

  return (
    <motion.button
      ref={ref}
      onClick={onClick}
      onMouseMove={handleMouseMove}
      onMouseLeave={handleMouseLeave}
      style={{ x: springX, y: springY }}
      whileTap={{ scale: 0.98 }}
      className={`relative flex items-center justify-center font-mono text-sm tracking-tight transition-colors overflow-hidden ${variants[variant]} ${fullWidth ? 'w-full' : ''} ${className}`}
    >
      {children}
    </motion.button>
  );
};

const FloatingCart = ({ cart, onRemove }) => {
  const [isExpanded, setIsExpanded] = useState(true);

  const oneTimeTotal = cart.filter(i => !i.recurring).reduce((s, i) => s + i.price, 0);
  const monthlyTotal = cart.filter(i => i.recurring).reduce((s, i) => s + i.price, 0);

  return (
    <AnimatePresence>
      {cart.length > 0 && (
        <motion.div
          key="floating-cart"
          initial={{ x: 400, opacity: 0 }}
          animate={{ x: 0, opacity: 1 }}
          exit={{ x: 400, opacity: 0 }}
          transition={{ type: 'spring', damping: 25, stiffness: 200 }}
          className="fixed right-8 top-24 w-96 bg-[#050505] border border-white/20 shadow-2xl z-50 flex flex-col max-h-[80vh] backdrop-blur-xl rounded-xl"
        >
          <div 
            className="p-4 border-b border-white/10 flex items-center justify-between cursor-pointer hover:bg-white/[0.02] transition-colors"
            onClick={() => setIsExpanded(!isExpanded)}
          >
            <div className="flex items-center gap-2">
              <Box className="w-4 h-4 text-white" />
              <span className="font-mono text-sm tracking-tight text-white uppercase">Your Stack</span>
              <span className="bg-white/10 text-white/80 text-[10px] px-2 py-0.5 ml-2 font-mono rounded">{cart.length}</span>
            </div>
            <ChevronRight className={`w-4 h-4 text-white/40 transition-transform ${isExpanded ? 'rotate-90' : '-rotate-90'}`} />
          </div>

          <AnimatePresence>
            {isExpanded && (
              <motion.div
                key="expanded-cart-content"
                initial={{ height: 0, opacity: 0 }}
                animate={{ height: 'auto', opacity: 1 }}
                exit={{ height: 0, opacity: 0 }}
                className="overflow-hidden flex flex-col"
              >
                <div className="flex-1 overflow-y-auto p-4 space-y-3 min-h-[100px] max-h-[40vh] custom-scrollbar">
                  {cart.map((item) => (
                    <div key={item.id} className="group relative pr-8">
                      <div className="flex justify-between items-start">
                        <span className="text-sm text-white/90 leading-tight pr-2 font-medium">{item.name}</span>
                        <span className="font-mono text-sm text-white flex-none">
                          {formatCurrency(item.price)}{item.recurring ? <span className="text-white/40 text-xs">/mo</span> : null}
                        </span>
                      </div>
                      {item.category && <span className={`text-[10px] uppercase tracking-widest ${item.color || 'text-white/40'}`}>{item.category}</span>}
                      <button 
                        onClick={() => onRemove(item.id)}
                        className="absolute right-0 top-0 p-1 opacity-0 group-hover:opacity-100 transition-opacity text-white/40 hover:text-white"
                      >
                        <X className="w-4 h-4" />
                      </button>
                      <div className="mt-3 border-b border-white/10 w-full" />
                    </div>
                  ))}
                </div>

                <div className="p-6 bg-white/[0.02] border-t border-white/10">
                  <div className="space-y-2 mb-6">
                    <div className="flex justify-between text-sm text-white/60 font-mono">
                      <span>One-time Build</span>
                      <span className="text-white">{formatCurrency(oneTimeTotal)}</span>
                    </div>
                    {monthlyTotal > 0 && (
                      <div className="flex justify-between text-sm text-blue-400 font-mono">
                        <span>Recurring</span>
                        <span>{formatCurrency(monthlyTotal)}/mo</span>
                      </div>
                    )}
                    <div className="border-t border-white/10 pt-4 mt-4 flex justify-between items-end">
                      <span className="text-sm tracking-tight text-white">Total Due Today</span>
                      <div className="text-right">
                        <span className="text-3xl font-light text-white tracking-tight leading-none">{formatCurrency(oneTimeTotal)}</span>
                        {monthlyTotal > 0 && <div className="text-[10px] text-white/40 font-mono mt-1">+ {formatCurrency(monthlyTotal)}/mo ongoing</div>}
                      </div>
                    </div>
                  </div>
                  
                  <MagneticButton fullWidth className="group !py-4 !bg-white !text-black !rounded-lg shadow-[0_0_40px_rgba(255,255,255,0.1)]">
                    Proceed to Checkout
                    <ArrowRight className="w-4 h-4 ml-2 group-hover:translate-x-1 transition-transform" />
                  </MagneticButton>
                </div>
              </motion.div>
            )}
          </AnimatePresence>
        </motion.div>
      )}
    </AnimatePresence>
  );
};

// ==========================================
// DYNAMIC SIMULATED SITES (V3 - Responsive & Category Aware)
// ==========================================

const SimulatedHVACSite = ({ arch, isMobile }) => {
  const [page, setPage] = useState('home');
  const [formStatus, setFormStatus] = useState('idle');

  const getIcon = (w = "w-5", h = "h-5") => {
    switch(arch.category) {
      case 'HVAC': return <ThermometerSun className={`${w} ${h} text-blue-600`} />;
      case 'Plumbing': return <Droplets className={`${w} ${h} text-cyan-600`} />;
      case 'Electrical': return <Zap className={`${w} ${h} text-yellow-500`} />;
      case 'Cleaning Services': return <Sparkles className={`${w} ${h} text-teal-500`} />;
      case 'Auto Repair': return <Car className={`${w} ${h} text-red-600`} />;
      default: return <Wrench className={`${w} ${h} text-slate-600`} />;
    }
  };

  const getHeroHeadline = () => {
    if (arch.category === 'Cleaning Services') return <>Spotless Results. <br/>Guaranteed <span className="text-teal-400">Every Time.</span></>;
    if (arch.category === 'Auto Repair') return <>Get Back on the Road. <br/>Fast, Honest <span className="text-red-400">Service.</span></>;
    return <>Don't Suffer. <br/>We Fix It <span className="text-blue-400">Today.</span></>;
  };

  const getHeroImage = () => {
    if (arch.category === 'Cleaning Services') return 'https://images.unsplash.com/photo-1581578731548-c64695cc6952?auto=format&fit=crop&w=2000&q=80';
    if (arch.category === 'Auto Repair') return 'https://images.unsplash.com/photo-1486262715619-67b85e0b08d3?auto=format&fit=crop&w=2000&q=80';
    if (arch.category === 'Electrical') return 'https://images.unsplash.com/photo-1621905251189-08b45d6a269e?auto=format&fit=crop&w=2000&q=80';
    return 'https://images.unsplash.com/photo-1581094288338-2314dddb7ece?auto=format&fit=crop&w=2000&q=80';
  };

  const handleForm = (e) => {
    e.preventDefault();
    setFormStatus('loading');
    setTimeout(() => setFormStatus('success'), 1200);
  };

  return (
    <div className="min-h-full bg-slate-50 text-slate-900 font-sans flex flex-col">
      {!isMobile && (
        <div className="bg-slate-900 text-slate-300 text-[10px] uppercase tracking-widest font-bold py-2 px-8 flex justify-between items-center">
          <div className="flex gap-6">
            <span className="flex items-center gap-2"><Shield className="w-3 h-3 text-emerald-400" /> Licensed, Bonded, Insured</span>
            <span className="flex items-center gap-2"><Star className="w-3 h-3 text-yellow-500" /> 4.9/5 Average Rating</span>
          </div>
          <div>Fast Dispatch: <span className="text-white">1-800-555-0199</span></div>
        </div>
      )}

      <nav className={`bg-white border-b border-slate-200 px-6 sm:px-8 flex items-center justify-between sticky top-0 z-50 ${isMobile ? 'h-16' : 'h-20'}`}>
        <div onClick={() => setPage('home')} className="flex items-center gap-3 font-black text-xl sm:text-2xl tracking-tighter text-slate-900 cursor-pointer">
          <div className="w-10 h-10 bg-slate-100 rounded-lg flex items-center justify-center">
            {getIcon("w-6", "h-6")}
          </div>
          <div className="leading-none">
            {arch.name.split(' ')[0]}<br/><span className="text-slate-500 text-sm tracking-widest">{arch.name.split(' ')[1] || 'SERVICES'}</span>
          </div>
        </div>
        
        {!isMobile ? (
          <div className="flex items-center gap-8 font-bold text-sm text-slate-600">
            <button onClick={() => setPage('home')} className={`hover:text-slate-900 transition-colors ${page==='home' ? 'text-slate-900' : ''}`}>Home</button>
            <button onClick={() => setPage('services')} className={`hover:text-slate-900 transition-colors ${page==='services' ? 'text-slate-900' : ''}`}>Services</button>
            <button onClick={() => setPage('contact')} className="bg-slate-900 text-white px-6 py-3 rounded-lg hover:bg-slate-800 transition-colors shadow-lg">
              Get an Estimate
            </button>
          </div>
        ) : (
          <Menu className="w-6 h-6 text-slate-900" />
        )}
      </nav>

      <div className="flex-1 flex flex-col overflow-y-auto custom-scrollbar">
        {page === 'home' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="flex-1 flex flex-col">
            <div className={`relative bg-slate-900 flex-none ${isMobile ? 'py-16 px-6' : 'py-32 px-16'}`}>
              <div className="absolute inset-0 bg-cover bg-center opacity-30 mix-blend-luminosity" style={{backgroundImage: `url('${getHeroImage()}')`}}></div>
              <div className="absolute inset-0 bg-gradient-to-r from-slate-900 via-slate-900/90 to-transparent"></div>
              <div className="relative z-10 max-w-2xl">
                <span className="bg-slate-800 border border-slate-700 text-white text-[10px] font-black tracking-widest uppercase px-3 py-1.5 rounded-md mb-6 inline-block">
                  #1 Local {arch.category} Company
                </span>
                <h1 className={`font-black tracking-tight text-white leading-[1.1] mb-6 ${isMobile ? 'text-4xl' : 'text-6xl'}`}>
                  {getHeroHeadline()}
                </h1>
                <p className="text-slate-300 text-lg font-medium mb-10 max-w-md">
                  {arch.tagline} Trusted by over 10,000 homeowners. Zero hidden fees. 100% satisfaction guarantee.
                </p>
                <button onClick={() => setPage('contact')} className="bg-white text-slate-900 font-black text-sm uppercase tracking-widest px-8 py-4 rounded-lg hover:bg-slate-100 transition-colors shadow-xl">
                  Book Service Now
                </button>
              </div>
            </div>
          </motion.div>
        )}

        {page === 'services' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className={`flex-1 bg-slate-50 ${isMobile ? 'p-6' : 'p-16'}`}>
            <h2 className="text-3xl font-black text-slate-900 mb-2">Expert Services</h2>
            <p className="text-slate-500 mb-10">Comprehensive solutions handled by certified professionals.</p>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              {[1, 2, 3, 4].map((s, i) => (
                <div key={i} className="bg-white p-8 border border-slate-200 rounded-xl hover:shadow-xl hover:border-slate-300 transition-all cursor-pointer">
                  <div className="w-12 h-12 bg-slate-50 rounded-lg flex items-center justify-center mb-6">{getIcon()}</div>
                  <h3 className="text-xl font-bold text-slate-900 mb-2">Core Service Option {i+1}</h3>
                  <p className="text-slate-600 text-sm leading-relaxed">High quality deployment of this service ensures long-lasting reliability and peak performance.</p>
                </div>
              ))}
            </div>
          </motion.div>
        )}

        {page === 'contact' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className={`flex-1 bg-slate-50 flex items-center justify-center ${isMobile ? 'p-6' : 'p-16'}`}>
            <div className="bg-white max-w-md w-full p-8 rounded-2xl shadow-xl border border-slate-200">
              <h2 className="text-2xl font-black text-slate-900 mb-2">Request Priority Service</h2>
              <p className="text-slate-500 text-sm mb-8">Submit your details. A dispatcher will text you within 60 seconds.</p>
              
              {formStatus === 'success' ? (
                <div className="py-12 text-center">
                  <div className="w-16 h-16 bg-green-100 text-green-600 rounded-full flex items-center justify-center mx-auto mb-4"><Check className="w-8 h-8"/></div>
                  <div className="text-xl font-bold text-slate-900">Request Confirmed</div>
                  <div className="text-slate-500 mt-2 text-sm">We are reviewing your details now. Expect a text message shortly.</div>
                  <button onClick={() => setFormStatus('idle')} className="mt-8 text-slate-900 font-bold text-sm">Submit Another</button>
                </div>
              ) : (
                <form onSubmit={handleForm} className="space-y-4">
                  <div>
                    <input required type="text" placeholder="Full Name" className="w-full bg-slate-50 border border-slate-200 px-4 py-3 rounded-lg focus:outline-none focus:border-slate-400" />
                  </div>
                  <div>
                    <input required type="tel" placeholder="Phone Number" className="w-full bg-slate-50 border border-slate-200 px-4 py-3 rounded-lg focus:outline-none focus:border-slate-400" />
                  </div>
                  <div>
                    <textarea required rows="3" placeholder="Describe the issue..." className="w-full bg-slate-50 border border-slate-200 px-4 py-3 rounded-lg focus:outline-none focus:border-slate-400 resize-none"></textarea>
                  </div>
                  <button type="submit" disabled={formStatus === 'loading'} className="w-full bg-slate-900 text-white font-bold py-4 rounded-lg mt-4 hover:bg-slate-800 transition-colors flex justify-center items-center">
                    {formStatus === 'loading' ? <div className="w-5 h-5 border-2 border-white border-t-transparent rounded-full animate-spin"></div> : 'Get an Estimate'}
                  </button>
                </form>
              )}
            </div>
          </motion.div>
        )}
        
        <footer className="bg-slate-900 text-slate-500 text-center py-8 text-xs flex-none">
          © 2026 {arch.name}. All rights reserved.
        </footer>
      </div>
    </div>
  );
};

const DemoContractor = ({ arch, isMobile }) => {
  const [page, setPage] = useState('home');

  const getIcon = () => arch.category === 'Solar' ? <Sun className="w-6 h-6 text-orange-500" /> : <Home className="w-6 h-6 text-orange-500" />;
  const getHeroImg = () => arch.category === 'Solar' ? 'https://images.unsplash.com/photo-1509391366360-12009a325852?auto=format&fit=crop&w=2000&q=80' : 'https://images.unsplash.com/photo-1632759145355-6d0c75ccbf97?auto=format&fit=crop&w=2000&q=80';

  return (
    <div className="min-h-full bg-white text-stone-900 font-sans flex flex-col selection:bg-orange-200">
      <nav className={`bg-stone-900 text-white flex items-center justify-between px-6 sm:px-8 sticky top-0 z-50 shadow-md ${isMobile ? 'h-16' : 'h-24'}`}>
        <div onClick={() => setPage('home')} className="flex items-center gap-2 font-black text-xl sm:text-2xl tracking-tight cursor-pointer uppercase">
          {getIcon()} {arch.name}
        </div>
        {!isMobile ? (
          <div className="flex items-center gap-8 font-bold text-sm text-stone-300">
            <button onClick={() => setPage('home')} className={`hover:text-white transition-colors ${page==='home' ? 'text-white' : ''}`}>Residential</button>
            <button onClick={() => setPage('services')} className={`hover:text-white transition-colors ${page==='services' ? 'text-white' : ''}`}>Commercial</button>
            <button className="bg-orange-500 text-black px-6 py-3 rounded-sm hover:bg-orange-400 transition-colors shadow-lg shadow-orange-500/20">
              Free Inspection
            </button>
          </div>
        ) : (
          <Menu className="w-6 h-6 text-white" />
        )}
      </nav>

      <div className="flex-1 flex flex-col overflow-y-auto custom-scrollbar">
        {page === 'home' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="flex-1 flex flex-col">
            <div className={`relative flex items-center bg-stone-900 ${isMobile ? 'min-h-[400px] px-6 py-12' : 'min-h-[600px] px-16'}`}>
              <div className="absolute inset-0 bg-cover bg-center opacity-40 mix-blend-luminosity" style={{backgroundImage: `url('${getHeroImg()}')`}}></div>
              <div className="absolute inset-0 bg-gradient-to-t from-stone-900 via-stone-900/50 to-transparent"></div>
              <div className="relative z-10 max-w-3xl text-white">
                <span className="bg-orange-500/20 border border-orange-500/50 text-orange-400 text-xs font-bold px-3 py-1 rounded-sm mb-6 inline-block tracking-widest uppercase">
                  Commercial & Residential
                </span>
                <h1 className={`font-black tracking-tight leading-[1.05] mb-6 ${isMobile ? 'text-4xl' : 'text-7xl'}`}>
                  Engineered to <br/> Withstand Anything.
                </h1>
                <p className="text-xl text-stone-300 font-medium mb-10 max-w-lg">
                  {arch.tagline} We build with industrial-grade materials backed by a 50-year ironclad warranty.
                </p>
                <div className="flex flex-wrap gap-4">
                  <button className="bg-orange-500 text-black font-black uppercase tracking-widest px-8 py-4 rounded-sm hover:bg-orange-400 transition-colors">
                    Start Your Project
                  </button>
                </div>
              </div>
            </div>
            <div className="bg-stone-100 py-12 px-6 sm:px-16 flex flex-col sm:flex-row gap-8 justify-between items-center border-b border-stone-200">
               <div className="text-xl font-bold font-serif italic text-stone-500">"The only contractor I will ever use again." - Forbes</div>
               <div className="flex gap-4">
                 <div className="w-12 h-12 bg-stone-200 rounded-full"></div>
                 <div className="w-12 h-12 bg-stone-200 rounded-full"></div>
                 <div className="w-12 h-12 bg-stone-200 rounded-full"></div>
               </div>
            </div>
          </motion.div>
        )}
      </div>
    </div>
  );
};

const SimulatedLuxurySite = ({ arch, isMobile }) => {
  const [page, setPage] = useState('home');

  const getImages = () => {
    if (arch.category === 'Real Estate') return ['https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?auto=format&fit=crop&w=2000&q=80'];
    if (arch.category === 'MedSpa') return ['https://images.unsplash.com/photo-1515377905703-c4788e51af15?auto=format&fit=crop&w=2000&q=80'];
    return ['https://images.unsplash.com/photo-1558904541-efa843a96f09?auto=format&fit=crop&w=2000&q=80']; // Landscaping
  };

  return (
    <div className="min-h-full bg-[#fcfbf9] text-stone-900 font-serif flex flex-col selection:bg-stone-200">
      <nav className={`bg-transparent px-8 flex items-center justify-between sticky top-0 z-50 transition-all backdrop-blur-sm ${isMobile ? 'h-20' : 'h-32'}`}>
        {!isMobile && <div className="w-1/3 flex gap-8 font-sans text-xs tracking-[0.2em] uppercase font-bold text-stone-500">
          <button onClick={() => setPage('home')} className={`hover:text-stone-900 ${page==='home'?'text-stone-900':''}`}>Portfolio</button>
          <button onClick={() => setPage('treatments')} className={`hover:text-stone-900 ${page==='treatments'?'text-stone-900':''}`}>Expertise</button>
        </div>}
        
        <div className="w-1/3 flex justify-center text-xl md:text-2xl tracking-[0.3em] uppercase font-light text-stone-900 text-center">
          {arch.name}
        </div>
        
        {!isMobile ? (
          <div className="w-1/3 flex justify-end">
            <button className="border border-stone-900 text-stone-900 font-sans text-[10px] tracking-[0.2em] uppercase font-bold px-8 py-3 hover:bg-stone-900 hover:text-white transition-colors">
              Inquire
            </button>
          </div>
        ) : (
          <Menu className="w-6 h-6 text-stone-900" />
        )}
      </nav>

      <div className="flex-1 flex flex-col overflow-y-auto custom-scrollbar">
        {page === 'home' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="flex-1 flex flex-col">
            <div className={`px-6 sm:px-16 pb-16 flex flex-col items-center text-center ${isMobile ? 'pt-8' : 'pt-16'}`}>
              <h1 className={`font-light text-stone-900 leading-tight mb-8 ${isMobile ? 'text-4xl' : 'text-6xl lg:text-7xl'}`}>
                Refined Elegance.<br/> Absolute Perfection.
              </h1>
              <div className={`w-full aspect-video bg-stone-200 relative overflow-hidden mb-16 ${isMobile ? 'h-[300px]' : 'max-w-5xl h-[600px]'}`}>
                <img src={getImages()[0]} className="w-full h-full object-cover" alt="Luxury Hero" />
              </div>
              <p className="max-w-2xl text-stone-500 font-sans text-sm sm:text-base leading-loose tracking-wide font-light">
                {arch.tagline} We cater to the most exclusive clientele, offering a bespoke experience that transcends the ordinary. Discover the art of absolute refinement.
              </p>
            </div>
          </motion.div>
        )}
        
        <footer className="py-12 text-center text-[10px] tracking-[0.3em] font-sans uppercase font-bold text-stone-400 border-t border-stone-200 mt-auto">
          {arch.name} © 2026
        </footer>
      </div>
    </div>
  );
};

const SimulatedCorporateSite = ({ arch, isMobile }) => {
  const [page, setPage] = useState('home');
  const isWealth = arch.category === 'Wealth Management';

  return (
    <div className="min-h-full bg-[#0a1128] text-white font-sans flex flex-col selection:bg-blue-500/30">
      <nav className={`border-b border-white/10 px-8 flex items-center justify-between sticky top-0 z-50 bg-[#0a1128]/90 backdrop-blur-md ${isMobile ? 'h-16' : 'h-24'}`}>
        <div onClick={() => setPage('home')} className="font-serif text-2xl tracking-tighter cursor-pointer flex items-center gap-3">
          {isWealth ? <LineChart className="w-6 h-6 text-blue-400" /> : <Scale className="w-6 h-6 text-amber-500" />}
          VANGUARD<span className={isWealth ? "text-blue-400" : "text-amber-500"}>.</span>
        </div>
        {!isMobile ? (
          <div className="flex items-center gap-8 text-xs font-bold tracking-widest uppercase text-white/60">
            <button onClick={() => setPage('home')} className={`hover:text-white transition-colors ${page==='home'?'text-white':''}`}>Firm Overview</button>
            <button onClick={() => setPage('results')} className={`hover:text-white transition-colors ${page==='results'?'text-white':''}`}>Our Record</button>
            <button className={`text-white px-6 py-3 rounded transition-colors ${isWealth ? 'bg-blue-600 hover:bg-blue-500' : 'bg-amber-600 hover:bg-amber-500'}`}>Private Consultation</button>
          </div>
        ) : (
          <Menu className="w-6 h-6 text-white" />
        )}
      </nav>

      <div className="flex-1 flex flex-col overflow-y-auto custom-scrollbar">
        {page === 'home' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="flex-1 flex flex-col">
            <div className={`relative ${isMobile ? 'py-16 px-6' : 'py-32 px-16'}`}>
              <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?auto=format&fit=crop&w=2000&q=80')] bg-cover bg-center opacity-20 mix-blend-luminosity"></div>
              <div className="absolute inset-0 bg-gradient-to-t from-[#0a1128] via-transparent to-transparent"></div>
              <div className="relative z-10 max-w-3xl">
                <div className={`w-12 h-1 mb-8 ${isWealth ? 'bg-blue-500' : 'bg-amber-500'}`}></div>
                <h1 className={`font-serif leading-[1.1] tracking-tight mb-8 ${isMobile ? 'text-4xl' : 'text-6xl lg:text-7xl'}`}>
                  {isWealth ? <>Protecting Legacies.<br/>Building <span className="text-blue-400 italic">Futures.</span></> : <>We Don't Settle.<br/>We <span className="text-amber-500 italic">Win.</span></>}
                </h1>
                <p className="text-lg text-white/60 font-light max-w-xl mb-10 leading-relaxed">
                  {arch.tagline} We represent individuals, families, and corporations with aggressive, sophisticated strategies.
                </p>
                <button className={`text-white text-xs font-bold tracking-widest uppercase px-8 py-4 rounded transition-colors ${isWealth ? 'bg-blue-600 hover:bg-blue-500' : 'bg-amber-600 hover:bg-amber-500'}`}>
                  View Our Approach
                </button>
              </div>
            </div>
          </motion.div>
        )}
      </div>
    </div>
  );
};

// --- APP DASHBOARDS (Multi-App Handlers) ---

const AppDashboard = ({ app, activeTab }) => {
  // THE DISPATCHER (Field Service)
  if (app.id === 'app-1') {
    if (activeTab === 'Leads') return (
      <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="space-y-6">
        <div className="grid grid-cols-1 sm:grid-cols-3 gap-4">
          {[ { l: 'NEW LEADS', v: '47' }, { l: 'PIPELINE VALUE', v: '$127K' }, { l: 'CLOSE RATE', v: '34%' } ].map((m, i) => (
            <div key={i} className="bg-[#0a0a0a] border border-white/10 rounded-xl p-6 flex flex-col hover:border-white/20 transition-colors">
              <span className="text-white/40 text-xs font-mono mb-2 tracking-widest uppercase">{m.l}</span>
              <span className="text-3xl font-light tracking-tight">{m.v}</span>
            </div>
          ))}
        </div>
        <div className="space-y-3">
          {[
            { n: 'John Anderson', d: 'HVAC Replacement Quote', t: '2m ago', active: true, amt: '$8,500' },
            { n: 'Sarah Jenkins', d: 'Emergency Pipe Leak', t: '14m ago', amt: 'Pending' },
            { n: 'Miller Commercial', d: 'Annual Maintenance Contract', t: '1h ago', amt: '$1,200' }
          ].map((l, i) => (
            <div key={i} className={`group bg-[#0a0a0a] border p-5 rounded-xl flex flex-col sm:flex-row sm:items-center justify-between gap-4 transition-colors cursor-pointer ${l.active ? 'border-purple-500/50 bg-purple-500/5' : 'border-white/10 hover:border-white/30'}`}>
              <div className="flex items-center gap-4">
                <div className={`w-10 h-10 rounded-full flex items-center justify-center font-mono text-sm ${l.active ? 'bg-purple-500 text-white shadow-[0_0_15px_rgba(168,85,247,0.4)]' : 'bg-white/10 text-white/60'}`}>{l.n.charAt(0)}</div>
                <div>
                  <div className="text-base text-white font-medium">{l.n}</div>
                  <div className="text-xs text-white/40 mt-1">{l.d}</div>
                </div>
              </div>
              <div className="flex items-center justify-between sm:flex-col sm:items-end gap-1">
                <div className="text-sm font-mono text-white/80">{l.amt}</div>
                <div className="text-[10px] text-white/40 font-mono tracking-widest uppercase">{l.t}</div>
              </div>
            </div>
          ))}
        </div>
      </motion.div>
    );

    if (activeTab === 'Calendar') return (
      <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="bg-[#0a0a0a] border border-white/10 rounded-xl p-6">
        <div className="grid grid-cols-7 gap-2">
          {['SUN','MON','TUE','WED','THU','FRI','SAT'].map((d,i) => <div key={i} className="text-center text-[10px] text-white/40 pb-4 font-mono tracking-widest">{d}</div>)}
          {[...Array(35)].map((_, i) => {
            const isWeekend = i % 7 === 0 || i % 7 === 6;
            const hasBooking = [12, 14, 15, 22, 28].includes(i);
            return (
              <div key={i} className={`h-24 border rounded-lg ${hasBooking ? 'border-purple-500/50 bg-purple-500/5' : 'border-white/5'} ${isWeekend ? 'bg-white/[0.01]' : 'bg-white/[0.03]'} p-3 transition-colors hover:border-white/20 cursor-pointer relative group`}>
                <span className={`text-xs font-mono ${hasBooking ? 'text-white' : 'text-white/40'}`}>{i + 1 > 31 ? (i-30) : i+1}</span>
                {hasBooking && (
                  <div className="absolute bottom-3 left-3 right-3 bg-purple-500 rounded px-2 py-1 flex items-center justify-between group-hover:bg-purple-400 transition-colors">
                    <span className="text-[8px] font-bold text-white uppercase hidden sm:block">Assigned</span>
                    <div className="w-1.5 h-1.5 bg-white rounded-full"></div>
                  </div>
                )}
              </div>
            );
          })}
        </div>
      </motion.div>
    );

    return <div className="h-64 flex items-center justify-center text-white/40 font-mono text-sm border border-dashed border-white/10 bg-[#0a0a0a] rounded-xl">Component Loading...</div>;
  }

  // PATIENT PORTAL OR CLIENT VAULT (Secure Docs)
  if (app.id === 'app-2' || app.id === 'app-3') {
    const isMedical = app.id === 'app-2';
    const accent = isMedical ? 'text-pink-400' : 'text-emerald-400';
    const borderAccent = isMedical ? 'hover:border-pink-500/30' : 'hover:border-emerald-500/30';

    if (activeTab === 'Documents' || activeTab === 'Vault') return (
      <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="space-y-6">
        <div className="border border-dashed border-white/20 bg-[#0a0a0a] p-12 flex flex-col items-center justify-center cursor-pointer hover:bg-white/[0.05] transition-colors rounded-xl group">
          <div className="w-16 h-16 rounded-full bg-white/5 flex items-center justify-center mb-4 group-hover:scale-110 transition-transform">
            <UploadCloud className={`w-8 h-8 text-white/40 transition-colors group-hover:${accent}`} />
          </div>
          <span className="text-sm text-white/80 font-mono tracking-tight mb-2">Drag & Drop Secure File</span>
          <span className="text-xs text-white/40">{isMedical ? 'HIPAA Compliant End-to-End Encryption' : '256-bit Bank-Grade Encryption'}</span>
        </div>
        <div className="grid grid-cols-1 sm:grid-cols-2 gap-4">
          {['Intake_Form_Signed.pdf', 'Identification_Front.jpg', isMedical ? 'Treatment_Plan_v2.pdf' : 'Tax_Returns_2025.pdf', isMedical ? 'XRay_Scan_01.png' : 'Trust_Agreement.pdf'].map((doc, i) => (
            <div key={i} className={`bg-[#0a0a0a] border border-white/10 p-5 flex items-center justify-between rounded-xl transition-colors cursor-pointer ${borderAccent}`}>
              <div className="flex items-center gap-4 overflow-hidden">
                <div className="w-10 h-10 rounded-lg bg-white/5 flex items-center justify-center flex-none">
                  <FileText className="w-5 h-5 text-white/60" />
                </div>
                <div className="overflow-hidden">
                  <div className="text-sm font-medium text-white truncate">{doc}</div>
                  <div className="text-xs text-white/40 font-mono mt-1">2.4 MB • Today</div>
                </div>
              </div>
            </div>
          ))}
        </div>
      </motion.div>
    );

    return <div className="h-64 flex items-center justify-center text-white/40 font-mono text-sm border border-dashed border-white/10 bg-[#0a0a0a] rounded-xl">Component Loading...</div>;
  }

  // CREW TRACKER (Construction)
  if (app.id === 'app-4') {
    if (activeTab === 'Map') return (
      <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="h-[500px] bg-[#0a0a0a] border border-white/10 rounded-xl relative overflow-hidden flex items-center justify-center">
         <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1524661135-423995f22d0b?auto=format&fit=crop&w=1000&q=80')] bg-cover bg-center opacity-30 grayscale"></div>
         <div className="absolute inset-0 bg-[#0a0a0a]/60 backdrop-blur-[2px]"></div>
         <div className="relative z-10 flex flex-col items-center">
            <MapPin className="w-12 h-12 text-orange-500 mb-4 animate-bounce" />
            <div className="bg-black/80 px-4 py-2 rounded text-xs font-mono uppercase tracking-widest text-white border border-white/10">3 Crews Active on Site</div>
         </div>
      </motion.div>
    );
    return <div className="h-64 flex items-center justify-center text-white/40 font-mono text-sm border border-dashed border-white/10 bg-[#0a0a0a] rounded-xl">Component Loading...</div>;
  }
  
  return null;
};

const SimulatedAppDispatcher = ({ app, isMobile }) => {
  const [tab, setTab] = useState(app.tabs[0].toLowerCase());
  
  const getIcon = (t) => {
    switch(t.toLowerCase()) {
      case 'leads': case 'documents': case 'map': return <LayoutGrid className="w-5 h-5" />;
      case 'calendar': case 'appointments': return <Calendar className="w-5 h-5" />;
      case 'vault': return <ShieldCheck className="w-5 h-5" />;
      default: return <Activity className="w-5 h-5" />;
    }
  };

  return (
    <div className="h-full w-full bg-[#0a0a0a] text-white flex flex-col font-sans">
      <div className="h-16 flex items-center justify-between px-6 border-b border-white/10 bg-[#121212] flex-none">
        <div className="flex items-center gap-3">
          <div className={`w-8 h-8 rounded-lg ${app.bg.replace('bg-', 'bg-').replace('-500', '-500/20')} ${app.color} flex items-center justify-center`}>
            {app.id === 'app-1' ? <Zap className="w-4 h-4" /> : app.id === 'app-4' ? <HardHat className="w-4 h-4" /> : <ShieldCheck className="w-4 h-4" />}
          </div>
          <div>
            <div className="text-[10px] font-bold tracking-widest uppercase text-white/40">{app.name}</div>
            <div className="text-sm font-medium">{tab.charAt(0).toUpperCase() + tab.slice(1)}</div>
          </div>
        </div>
        <div className="w-8 h-8 rounded-full bg-white/10 flex items-center justify-center">
          <Users className="w-4 h-4 text-white/60" />
        </div>
      </div>

      <div className="flex-1 overflow-y-auto custom-scrollbar p-6 bg-[#050505]">
         <AppDashboard app={app} activeTab={app.tabs.find(t => t.toLowerCase() === tab) || app.tabs[0]} />
      </div>

      <div className="h-20 bg-[#121212] border-t border-white/10 flex justify-around items-center px-4 pb-4 flex-none">
        {app.tabs.slice(0, 2).map((t, i) => (
          <button key={i} onClick={() => setTab(t.toLowerCase())} className={`flex flex-col items-center gap-1 ${tab === t.toLowerCase() ? app.color : 'text-white/40'}`}>
            {getIcon(t)}
            <span className="text-[9px] uppercase tracking-widest font-bold">{t}</span>
          </button>
        ))}
        <button className={`w-12 h-12 rounded-full ${app.bg} text-white flex items-center justify-center -mt-6 shadow-[0_0_20px_rgba(255,255,255,0.1)]`}>
          <Plus className="w-6 h-6" />
        </button>
        {app.tabs.slice(2, 4).map((t, i) => (
          <button key={i} onClick={() => setTab(t.toLowerCase())} className={`flex flex-col items-center gap-1 ${tab === t.toLowerCase() ? app.color : 'text-white/40'}`}>
            {getIcon(t)}
            <span className="text-[9px] uppercase tracking-widest font-bold">{t}</span>
          </button>
        ))}
      </div>
    </div>
  );
};


// ==========================================
// INTERACTIVE TRIAL MODAL
// ==========================================

const InteractiveTrialModal = ({ architecture, onClose, onSelect }) => {
  const [isMobile, setIsMobile] = useState(false);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    if (architecture) {
      setIsLoading(true);
      const t = setTimeout(() => setIsLoading(false), 800);
      return () => clearTimeout(t);
    }
  }, [architecture, isMobile]);

  if (!architecture) return null;

  const renderDemoSite = () => {
    if (architecture.id.includes('app')) return <SimulatedAppDispatcher app={architecture} isMobile={isMobile} />;
    if (['HVAC', 'Plumbing', 'Electrical', 'Cleaning Services', 'Auto Repair'].includes(architecture.category)) return <SimulatedHVACSite arch={architecture} isMobile={isMobile} />;
    if (['MedSpa', 'Luxury Landscaping', 'Real Estate'].includes(architecture.category)) return <SimulatedLuxurySite arch={architecture} isMobile={isMobile} />;
    if (['Legal', 'Wealth Management'].includes(architecture.category)) return <SimulatedCorporateSite arch={architecture} isMobile={isMobile} />;
    return <DemoContractor arch={architecture} isMobile={isMobile} />;
  };

  return (
    <AnimatePresence>
      <motion.div
        key="modal-overlay"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        exit={{ opacity: 0 }}
        transition={{ duration: 0.2 }}
        className="fixed inset-0 z-50 flex flex-col bg-[#050505]/95 backdrop-blur-2xl"
      >
        {/* HEADER */}
        <div className="flex-none h-20 border-b border-white/10 flex items-center justify-between px-8 bg-[#050505]">
          <div>
            <span className={`text-[10px] font-mono tracking-widest uppercase ${architecture.color}`}>{architecture.category}</span>
            <h2 className="text-2xl font-light tracking-tight text-white mt-1">{architecture.name}</h2>
          </div>
          
          <div className="flex items-center bg-white/5 border border-white/10 p-1 rounded-sm gap-1">
            <button onClick={() => setIsMobile(false)} className={`p-2 transition-colors rounded-sm ${!isMobile ? 'bg-white/10 text-white shadow-sm' : 'text-white/40 hover:text-white'}`}>
              <Monitor className="w-4 h-4" />
            </button>
            <button onClick={() => setIsMobile(true)} className={`p-2 transition-colors rounded-sm ${isMobile ? 'bg-white/10 text-white shadow-sm' : 'text-white/40 hover:text-white'}`}>
              <Smartphone className="w-4 h-4" />
            </button>
          </div>

          <button onClick={onClose} className="p-2 text-white/40 hover:text-white transition-colors bg-white/5 rounded-full hover:bg-white/10">
            <X className="w-5 h-5" />
          </button>
        </div>

        {/* METRICS BAR */}
        <div className="flex-none h-14 border-b border-white/5 bg-gradient-to-r from-white/[0.02] to-transparent flex items-center px-8 gap-12 overflow-x-auto">
          {[
            { l: 'LOAD TIME', v: `${architecture.loadTime}s` },
            { l: 'CONVERSION RATE', v: `${architecture.conversionRate}%` },
            { l: 'MOBILE OPTIMIZED', v: 'True' },
            { l: 'SEO SCORE', v: '99/100' }
          ].map((m, i) => (
            <div key={i} className="flex flex-col">
              <span className="text-[10px] font-mono text-white/40 tracking-widest">{m.l}</span>
              <span className="text-sm text-white font-mono">{m.v}</span>
            </div>
          ))}
        </div>

        {/* DEMO BROWSER AREA */}
        <div className="flex-grow p-4 sm:p-8 flex items-center justify-center overflow-hidden relative bg-[#030303]">
          <div className={`absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] ${architecture.bg} opacity-[0.03] blur-[100px] rounded-full pointer-events-none`}></div>
          
          <motion.div
            layout
            initial={false}
            animate={{ width: isMobile ? 375 : '100%', maxWidth: isMobile ? 375 : 1200, height: isMobile ? 750 : '100%' }}
            className={`bg-[#0a0a0a] border shadow-[0_0_60px_rgba(0,0,0,0.5)] relative z-10 flex flex-col overflow-hidden transition-all duration-300 ${isMobile ? 'rounded-[48px] border-[8px] border-[#1a1a1a]' : 'rounded-xl border-white/10'}`}
          >
            {/* Device Specific Chrome */}
            {!isMobile ? (
              <div className="h-12 border-b border-white/10 bg-[#121212] flex items-center px-4 gap-4 flex-none">
                <div className="flex gap-2">
                  <div className="w-3 h-3 rounded-full bg-red-500/20 border border-red-500/50"></div>
                  <div className="w-3 h-3 rounded-full bg-yellow-500/20 border border-yellow-500/50"></div>
                  <div className="w-3 h-3 rounded-full bg-green-500/20 border border-green-500/50"></div>
                </div>
                <div className="mx-auto text-[10px] font-mono text-white/30 bg-[#050505] border border-white/5 px-32 py-1.5 rounded-md hidden sm:block shadow-inner">
                  https://demo.{architecture.category.toLowerCase().replace(/[^a-z0-9]/g, '')}.nexus.waas
                </div>
              </div>
            ) : (
              <div className="absolute top-0 left-1/2 -translate-x-1/2 w-32 h-6 bg-[#1a1a1a] rounded-b-2xl z-50"></div>
            )}

            {/* Simulated Content Wrapper */}
            <div className={`flex-grow bg-[#050505] relative overflow-hidden flex flex-col ${isMobile ? 'pt-8 pb-4 px-2' : ''}`}>
              {isLoading ? (
                <div className="absolute inset-0 flex flex-col items-center justify-center text-white/40 gap-4">
                  <div className={`w-8 h-8 border-2 border-white/10 ${architecture.border || 'border-blue-500'} border-t-transparent rounded-full animate-spin`}></div>
                  <span className="font-mono text-xs tracking-widest uppercase">Rendering DOM...</span>
                </div>
              ) : (
                <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className={`h-full flex flex-col overflow-y-auto custom-scrollbar ${isMobile ? 'rounded-[32px] overflow-hidden mask-image-rounded' : ''}`}>
                   {renderDemoSite()}
                </motion.div>
              )}
            </div>
          </motion.div>
        </div>

        {/* BOTTOM ACTION BAR */}
        <div className="flex-none h-24 border-t border-white/10 bg-[#050505] flex items-center justify-between px-8 z-20">
          <div className="hidden sm:flex items-center gap-3 text-white/40">
            <Cpu className="w-5 h-5" />
            <span className="text-sm tracking-tight font-mono uppercase">Live Virtual Environment Rendered</span>
          </div>
          
          <div className="w-full sm:w-auto">
            <MagneticButton onClick={() => { onSelect(architecture); onClose(); }} fullWidth>
              Select This Architecture <span className="mx-2 opacity-30">•</span> {formatCurrency(architecture.basePrice)}
            </MagneticButton>
          </div>
        </div>
      </motion.div>
    </AnimatePresence>
  );
};

// ==========================================
// MAIN DASHBOARD LAYOUT (3-PANE)
// ==========================================

export default function App() {
  const [activeItem, setActiveItem] = useState(ARCHITECTURES[0]);
  const [viewMode, setViewMode] = useState('desktop'); 
  const [cart, setCart] = useState([]);
  const [selectedAddOns, setSelectedAddOns] = useState([]);
  
  const addToCart = (item) => {
    if (!cart.find(c => c.id === item.id)) {
      setCart([...cart, { ...item, price: item.basePrice || item.price }]);
    }
  };

  const removeFromCart = (id) => {
    setCart(cart.filter(c => c.id !== id));
    setSelectedAddOns(selectedAddOns.filter(a => a.id !== id));
  };

  const toggleAddOn = (addon) => {
    if (cart.find(c => c.id === addon.id)) {
      removeFromCart(addon.id);
    } else {
      addToCart(addon);
      setSelectedAddOns([...selectedAddOns, addon]);
    }
  };

  // Render the correct simulated UI based on selection in the main view
  const renderSimulatedUI = () => {
    if (activeItem.id.includes('app')) return <SimulatedAppDispatcher app={activeItem} isMobile={true} />;
    if (['HVAC', 'Plumbing', 'Electrical', 'Cleaning Services', 'Auto Repair'].includes(activeItem.category)) return <SimulatedHVACSite arch={activeItem} isMobile={viewMode === 'mobile'} />;
    if (['MedSpa', 'Luxury Landscaping', 'Real Estate'].includes(activeItem.category)) return <SimulatedLuxurySite arch={activeItem} isMobile={viewMode === 'mobile'} />;
    if (['Legal', 'Wealth Management'].includes(activeItem.category)) return <SimulatedCorporateSite arch={activeItem} isMobile={viewMode === 'mobile'} />;
    return <DemoContractor arch={activeItem} isMobile={viewMode === 'mobile'} />;
  };

  const isApp = activeItem.id.includes('app');
  const currentViewMode = isApp ? 'mobile' : viewMode;

  return (
    <div className="h-screen w-screen overflow-hidden bg-[#050505] text-white font-sans flex selection:bg-white/20 selection:text-white">
      <FloatingCart cart={cart} onRemove={removeFromCart} />
      
      {/* ==========================================
          PANE 1: LEFT SIDEBAR (NAVIGATION)
          ========================================== */}
      <aside className="w-72 border-r border-white/[0.06] bg-[#020202] flex flex-col z-20 flex-none relative">
        <div className="p-6 border-b border-white/[0.06]">
          <div className="flex items-center gap-3">
            <div className="w-6 h-6 bg-white flex items-center justify-center">
              <Zap className="w-4 h-4 text-black" />
            </div>
            <span className="font-mono text-xs tracking-[0.2em] uppercase font-bold text-white/90">Nexus<span className="text-white/40">_OS</span></span>
          </div>
        </div>

        <div className="flex-1 overflow-y-auto custom-scrollbar p-4 space-y-8">
          
          {/* Section: Web Architectures */}
          <div>
            <div className="text-[10px] font-mono tracking-widest text-white/40 uppercase mb-3 px-2">Web Architectures ({ARCHITECTURES.length})</div>
            <div className="space-y-1">
              {ARCHITECTURES.map((arch) => (
                <button 
                  key={arch.id}
                  onClick={() => setActiveItem(arch)}
                  className={`w-full text-left px-3 py-2.5 rounded flex items-center justify-between transition-colors ${activeItem.id === arch.id ? 'bg-white/[0.08] text-white' : 'text-white/50 hover:bg-white/[0.02] hover:text-white'}`}
                >
                  <span className="text-sm font-medium tracking-tight truncate pr-4">{arch.name}</span>
                  {activeItem.id === arch.id && <div className={`w-1.5 h-1.5 rounded-full ${arch.bg} shadow-[0_0_8px_currentColor]`}></div>}
                </button>
              ))}
            </div>
          </div>

          {/* Section: Field Apps */}
          <div>
            <div className="text-[10px] font-mono tracking-widest text-white/40 uppercase mb-3 px-2">Field Operations ({APPS.length})</div>
            <div className="space-y-1">
              {APPS.map((app) => (
                <button 
                  key={app.id}
                  onClick={() => setActiveItem(app)}
                  className={`w-full text-left px-3 py-2.5 rounded flex items-center justify-between transition-colors ${activeItem.id === app.id ? 'bg-white/[0.08] text-white' : 'text-white/50 hover:bg-white/[0.02] hover:text-white'}`}
                >
                  <span className="text-sm font-medium tracking-tight">{app.name}</span>
                  {activeItem.id === app.id && <div className={`w-1.5 h-1.5 rounded-full ${app.bg} shadow-[0_0_8px_currentColor]`}></div>}
                </button>
              ))}
            </div>
          </div>
        </div>

        <div className="p-4 border-t border-white/[0.06] flex items-center gap-3 text-white/40 hover:text-white transition-colors cursor-pointer">
          <div className="w-8 h-8 rounded-full bg-white/5 flex items-center justify-center">
            <Users className="w-4 h-4" />
          </div>
          <div className="text-xs font-mono">Partner Portal</div>
        </div>
      </aside>

      {/* ==========================================
          PANE 2: CENTER STAGE (HARDWARE SHOWCASE)
          ========================================== */}
      <main className="flex-1 bg-[#0a0a0a] relative flex flex-col overflow-hidden">
        {/* Cinematic Backdrop */}
        <div className="absolute inset-0 pointer-events-none z-0 overflow-hidden">
          <div className={`absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] ${activeItem.bg} opacity-[0.02] blur-[100px] rounded-full transition-colors duration-1000`}></div>
          <div className="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDAiIGhlaWdodD0iNDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGRlZnM+PHBhdHRlcm4gaWQ9ImdyaWQiIHdpZHRoPSI0MCIgaGVpZ2h0PSI0MCIgcGF0dGVyblVuaXRzPSJ1c2VyU3BhY2VPblVzZSI+PHBhdGggZD0iTSA0MCAwIEwgMCAwIDAgNDAiIGZpbGw9Im5vbmUiIHN0cm9rZT0id2hpdGUiIHN0cm9rZS1vcGFjaXR5PSIwLjAyIiBzdHJva2Utd2lkdGg9IjEiLz48L3BhdHRlcm4+PC9kZWZzPjxyZWN0IHdpZHRoPSIxMDAlIiBoZWlnaHQ9IjEwMCUiIGZpbGw9InVybCgjZ3JpZCkiLz48L3N2Zz4=')] opacity-50"></div>
        </div>

        {/* View Controls */}
        <div className="absolute top-6 left-1/2 -translate-x-1/2 z-20 flex bg-white/5 border border-white/10 p-1 rounded-md backdrop-blur-md">
          <button 
            onClick={() => !isApp && setViewMode('desktop')} 
            className={`p-2 px-4 rounded flex items-center gap-2 text-xs font-mono tracking-widest transition-all ${currentViewMode === 'desktop' ? 'bg-white/10 text-white shadow-sm' : 'text-white/40 hover:text-white'} ${isApp ? 'opacity-30 cursor-not-allowed' : ''}`}
          >
            <Monitor className="w-3.5 h-3.5" /> Desktop
          </button>
          <button 
            onClick={() => setViewMode('mobile')} 
            className={`p-2 px-4 rounded flex items-center gap-2 text-xs font-mono tracking-widest transition-all ${currentViewMode === 'mobile' ? 'bg-white/10 text-white shadow-sm' : 'text-white/40 hover:text-white'}`}
          >
            <Smartphone className="w-3.5 h-3.5" /> Mobile
          </button>
        </div>

        {/* Hardware Mockup Container */}
        <div className="flex-1 flex items-center justify-center p-12 relative z-10">
          <AnimatePresence mode="wait">
            <motion.div
              key={`${activeItem.id}-${currentViewMode}`}
              initial={{ opacity: 0, scale: 0.98, y: 10 }}
              animate={{ opacity: 1, scale: 1, y: 0 }}
              exit={{ opacity: 0, scale: 0.98, y: -10 }}
              transition={{ duration: 0.3, ease: [0.22, 1, 0.36, 1] }}
              className={`relative flex flex-col shadow-[0_40px_80px_rgba(0,0,0,0.8)] border-white/10 ${
                currentViewMode === 'mobile' 
                  ? 'w-[340px] h-[720px] bg-black border-[8px] border-[#1a1a1a] rounded-[48px] overflow-hidden' 
                  : 'w-full max-w-[1000px] h-[700px] bg-black border rounded-xl overflow-hidden'
              }`}
            >
              {currentViewMode === 'desktop' ? (
                <div className="h-10 bg-[#1a1a1a] border-b border-white/5 flex items-center px-4 flex-none">
                  <div className="flex gap-2">
                    <div className="w-3 h-3 rounded-full bg-white/10 border border-white/10"></div>
                    <div className="w-3 h-3 rounded-full bg-white/10 border border-white/10"></div>
                    <div className="w-3 h-3 rounded-full bg-white/10 border border-white/10"></div>
                  </div>
                  <div className="mx-auto text-[10px] font-mono text-white/30 bg-black/50 px-32 py-1 rounded shadow-inner">
                    https://preview.nexus.waas/{activeItem.category.toLowerCase().replace(/[^a-z0-9]/g, '')}
                  </div>
                </div>
              ) : (
                <div className="absolute top-0 left-1/2 -translate-x-1/2 w-32 h-6 bg-[#1a1a1a] rounded-b-3xl z-50"></div>
              )}

              <div className={`flex-1 bg-black overflow-hidden relative ${currentViewMode === 'mobile' ? 'pt-6' : ''}`}>
                {renderSimulatedUI()}
              </div>
            </motion.div>
          </AnimatePresence>
        </div>
      </main>

      {/* ==========================================
          PANE 3: RIGHT PANEL (SALES & CART)
          ========================================== */}
      <aside className="w-96 border-l border-white/[0.06] bg-[#020202] flex flex-col z-20 flex-none relative">
        <AnimatePresence mode="wait">
          <motion.div 
            key={activeItem.id}
            initial={{ opacity: 0, x: 20 }}
            animate={{ opacity: 1, x: 0 }}
            exit={{ opacity: 0, x: -20 }}
            transition={{ duration: 0.2 }}
            className="flex-1 overflow-y-auto custom-scrollbar p-8 flex flex-col"
          >
            <div className={`text-[10px] font-mono tracking-[0.2em] uppercase mb-4 ${activeItem.color}`}>
              {activeItem.category}
            </div>
            <h2 className="text-4xl font-light tracking-tight text-white mb-4 leading-none">
              {activeItem.name}
            </h2>
            <p className="text-white/50 text-sm leading-relaxed mb-8">
              {activeItem.tagline} Designed for elite operations that demand maximum conversion velocity.
            </p>

            <div className="grid grid-cols-2 gap-4 mb-8">
              <div className="bg-white/[0.02] border border-white/[0.06] p-4 rounded-lg">
                <div className="text-[10px] font-mono uppercase tracking-widest text-white/40 mb-1">Load Speed</div>
                <div className="text-2xl font-light">{activeItem.loadTime}s</div>
              </div>
              <div className="bg-white/[0.02] border border-white/[0.06] p-4 rounded-lg">
                <div className="text-[10px] font-mono uppercase tracking-widest text-white/40 mb-1">Conv. Rate</div>
                <div className="text-2xl font-light text-green-400">{activeItem.conversionRate}%</div>
              </div>
            </div>

            <div className="space-y-4 mb-8">
              <div className="text-[10px] font-mono tracking-widest text-white/40 uppercase border-b border-white/[0.06] pb-2">Technical Capabilities</div>
              {activeItem.features.map((feat, i) => (
                <div key={i} className="flex items-start gap-3">
                  <div className={`mt-0.5 w-4 h-4 rounded-full flex items-center justify-center bg-white/5 border border-white/10 flex-none`}>
                    <Check className={`w-2.5 h-2.5 ${activeItem.color}`} />
                  </div>
                  <span className="text-sm text-white/80">{feat}</span>
                </div>
              ))}
            </div>

            <div className="flex-1"></div>

            <div className="border-t border-white/[0.06] pt-8 mt-8">
              <div className="flex items-end justify-between mb-6">
                <div>
                  <div className="text-[10px] font-mono tracking-widest text-white/40 uppercase mb-1">Investment</div>
                  <div className="text-3xl font-light">{formatCurrency(activeItem.basePrice)}</div>
                </div>
                {activeItem.recurring && <div className="text-xs text-white/40 font-mono">/ month</div>}
              </div>

              <MagneticButton 
                onClick={() => addToCart(activeItem)}
                fullWidth 
                className="group !py-4 !bg-white !text-black !rounded-lg shadow-[0_0_40px_rgba(255,255,255,0.1)]"
              >
                Acquire System
                <ArrowRight className="w-4 h-4 ml-2 group-hover:translate-x-1 transition-transform" />
              </MagneticButton>
            </div>
          </motion.div>
        </AnimatePresence>
      </aside>

    </div>
  );
}
