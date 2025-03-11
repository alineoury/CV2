// 1. package.json
{
  "name": "ux-cv",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "framer-motion": "^10.0.0",
    "react": "^18.0.0",
    "react-dom": "^18.0.0",
    "react-scroll": "^1.8.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.0.0",
    "tailwindcss": "^3.0.0",
    "vite": "^5.0.0"
  }
}

// 2. tailwind.config.js
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};

// 3. main.jsx
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import Portfolio from "./Portfolio";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <Portfolio />
  </React.StrictMode>
);

// 4. index.css
@tailwind base;
@tailwind components;
@tailwind utilities;

// 5. Portfolio.jsx
import { motion } from "framer-motion";
import { Link } from "react-scroll";

const sections = [
  { id: "about", title: "Über mich" },
  { id: "portfolio", title: "Portfolio" },
  { id: "experience", title: "Erfahrung" },
  { id: "contact", title: "Kontakt" },
];

export default function Portfolio() {
  return (
    <div className="font-sans bg-gray-100 text-gray-900">
      <header className="fixed top-0 left-0 w-full bg-white shadow-md p-4 flex justify-between items-center">
        <h1 className="text-xl font-bold">Mein UX Portfolio</h1>
        <nav>
          {sections.map((section) => (
            <Link key={section.id} to={section.id} smooth={true} className="mx-2 cursor-pointer hover:text-blue-500">
              {section.title}
            </Link>
          ))}
        </nav>
      </header>
      
      <main className="pt-20">
        {sections.map((section) => (
          <Section key={section.id} id={section.id} title={section.title}>
            <p>Hier kommt der Inhalt für {section.title}.</p>
          </Section>
        ))}
      </main>
    </div>
  );
}

function Section({ id, title, children }) {
  return (
    <motion.section
      id={id}
      className="min-h-screen flex flex-col justify-center items-center p-10"
      initial={{ opacity: 0, y: 50 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5 }}
    >
      <h2 className="text-3xl font-bold mb-4">{title}</h2>
      {children}
    </motion.section>
  );
}
