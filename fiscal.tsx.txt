import React, { useState } from 'react';
import { Camera, Send, CheckCircle } from 'lucide-react';

export default function FiscalApp() {
  const [enviado, setEnviado] = useState(false);

  return (
    <div className="max-w-md mx-auto p-4 bg-gray-50 min-h-screen font-sans">
      <header className="bg-blue-700 text-white p-4 rounded-b-xl mb-6 shadow-lg">
        <h1 className="text-xl font-bold text-center">SAGME - FISCALIZAÇÃO</h1>
        <p className="text-sm text-center opacity-80">Registro de Ocorrência Técnica</p>
      </header>

      {!enviado ? (
        <div className="space-y-4">
          <div className="bg-white p-4 rounded-lg shadow">
            <label className="block text-sm font-medium text-gray-700 mb-1">Unidade/Prédio</label>
            <select className="w-full border p-2 rounded bg-gray-50">
              <option>Reitoria / CLA</option>
              <option>Nutrição / Biblioteconomia</option>
              <option>IB / Enfermagem</option>
              <option>Medicina / CCJP</option>
            </select>
          </div>

          <div className="bg-white p-4 rounded-lg shadow">
            <label className="block text-sm font-medium text-gray-700 mb-1">Foto da Ordem de Serviço (OS)</label>
            <button className="w-full h-32 border-2 border-dashed border-gray-300 rounded-lg flex flex-col items-center justify-center text-gray-500 hover:bg-gray-50">
              <Camera size={32} />
              <span className="text-xs mt-2 font-semibold">TIRAR FOTO AGORA</span>
            </button>
          </div>

          <button 
            onClick={() => setEnviado(true)}
            className="w-full bg-blue-600 text-white font-bold py-4 rounded-lg shadow-lg flex items-center justify-center gap-2 active:bg-blue-800"
          >
            <Send size={20} /> ENVIAR CHAMADO
          </button>
        </div>
      ) : (
        <div className="text-center py-20 bg-white rounded-xl shadow-xl px-6">
          <CheckCircle className="text-green-500 mx-auto mb-4" size={64} />
          <h2 className="text-2xl font-bold text-gray-800">Enviado com Sucesso!</h2>
          <p className="text-gray-600 mt-2">A Auditoria foi registrada e o SLA de 30min/2h começou a contar.</p>
          <button onClick={() => setEnviado(false)} className="mt-6 text-blue-600 font-semibold underline">Registrar novo chamado</button>
        </div>
      )}
    </div>
  );
}