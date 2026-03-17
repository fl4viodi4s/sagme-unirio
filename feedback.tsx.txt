import React, { useState } from 'react';

export default function NPSPage() {
  const [nota, setNota] = useState<number | null>(null);

  return (
    <div className="min-h-screen bg-yellow-400 flex flex-col items-center justify-center p-6 text-center">
      <div className="bg-white p-8 rounded-3xl shadow-2xl max-w-sm w-full border-4 border-black">
        <h1 className="text-3xl font-black mb-2">OPINE! 🛗</h1>
        <p className="text-gray-600 font-bold mb-6 italic">Como está o funcionamento deste elevador?</p>
        
        <div className="grid grid-cols-5 gap-2 mb-6">
          {[1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map((n) => (
            <button
              key={n}
              onClick={() => setNota(n)}
              className={`h-12 w-full font-black border-2 border-black rounded transition-all ${
                nota === n ? 'bg-black text-white' : 'bg-gray-100 hover:bg-yellow-200'
              }`}
            >
              {n}
            </button>
          ))}
        </div>

        {nota && (
          <button className="w-full bg-green-500 text-white font-black py-4 border-4 border-black rounded-xl shadow-[5px_5px_0px_0px_rgba(0,0,0,1)] active:shadow-none translate-x-1">
            ENVIAR MINHA NOTA!
          </button>
        )}
      </div>
    </div>
  );
}