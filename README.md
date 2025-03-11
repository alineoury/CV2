import { motion } from 'framer-motion';
import { useState } from 'react';
import { Link } from 'react-scroll';

const sections = [
  { id: 'about', title: 'Über mich' },
  { id: 'portfolio', title: 'Portfolio' },
  { id: 'experience', title: 'Erfahrung' },
  { id: 'contact', title: 'Kontakt' },
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
        <Section id="about" title="Über mich">
          <p>Ich bin eine UX-Designerin mit Leidenschaft für intuitive und ansprechende Nutzererlebnisse.</p>
        </Section>
        
        <Section id="portfolio" title="Portfolio">
          <p>Hier präsentiere ich einige meiner erfolgreich umgesetzten Projekte.</p>
        </Section>

        <Section id="experience" title="Erfahrung">
          <p>Meine beruflichen Stationen und Erfolge als UX-Expertin.</p>
        </Section>

        <Section id="contact" title="Kontakt">
          <p>Hier kannst du mich erreichen: E-Mail oder LinkedIn.</p>
        </Section>
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
