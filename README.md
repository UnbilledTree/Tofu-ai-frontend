// pages/index.js (Next.js Frontend for Tofu AI) import { useState } from "react";

export default function Home() { const [prompt, setPrompt] = useState(""); const [image, setImage] = useState(null); const [loading, setLoading] = useState(false);

const handleGenerate = async () => { setLoading(true); const res = await fetch("https://your-api-url.com/generate?prompt=" + encodeURIComponent(prompt)); const data = await res.json(); setImage("data:image/png;base64," + data.image); setLoading(false); };

return ( <div className="min-h-screen flex flex-col items-center justify-center p-4"> <h1 className="text-4xl font-bold mb-6">Tofu AI</h1> <input type="text" placeholder="Type your prompt..." value={prompt} onChange={(e) => setPrompt(e.target.value)} className="border p-2 rounded w-full max-w-md mb-4" /> <button
onClick={handleGenerate}
disabled={loading}
className="bg-blue-600 text-white px-4 py-2 rounded shadow"
> {loading ? "Generating..." : "Generate Image"} </button> {image && ( <img
src={image}
alt="Generated"
className="mt-6 w-full max-w-lg rounded shadow"
/> )} </div> ); }

