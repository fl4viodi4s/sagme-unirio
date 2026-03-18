import React from 'react';
import { BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer } from 'recharts';
import { AlertTriangle, CheckCircle, Clock } from 'lucide-react';

const data = [
  { name: 'Reitoria', total: 4, operantes: 4, parados: 0 },
  { name: 'Nutrição', total: 5, operantes: 5, parados: 0 },
  { name: 'Enfermagem', total: 8, operantes: 7, parados: 1 },
  { name: 'Medicina', total: 2, operantes: 2, parados: 0 },
];

export default function Dashboard() {
  return (
    <div className="p-6 bg-gray-50 min-h-screen">
      <h1 className="text-2xl font-bold mb-6">SAGME - Dashboard de Auditoria (UNIRIO)</h1>
      
      <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
        <div className="bg-white p-4 rounded-lg shadow border-l-4 border-blue-500">
          <div className="flex items-center">
            <Clock className="text-blue-500 mr-2" />
            <span>Total de Elevadores: 19</span>
          </div>
        </div>
        <div className="bg-white p-4 rounded-lg shadow border-l-4 border-green-500">
          <div className="flex items-center">
            <CheckCircle className="text-green-500 mr-2" />
            <span>Operantes: 18</span>
          </div>
        </div>
        <div className="bg-white p-4 rounded-lg shadow border-l-4 border-red-500">
          <div className="flex items-center">
            <AlertTriangle className="text-red-500 mr-2" />
            <span>Parados (Fora de SLA): 1</span>
          </div>
        </div>
      </div>

      <div className="bg-white p-6 rounded-lg shadow mb-6">
        <h2 className="text-xl font-semibold mb-4">Status por Unidade</h2>
        <div className="h-64">
          <ResponsiveContainer width="100%" height="100%">
            <BarChart data={data}>
              <CartesianGrid strokeDasharray="3 3" />
              <XAxis dataKey="name" />
              <YAxis />
              <Tooltip />
              <Bar dataKey="operantes" fill="#10b981" name="Operantes" />
              <Bar dataKey="parados" fill="#ef4444" name="Parados" />
            </BarChart>
          </ResponsiveContainer>
        </div>
      </div>
    </div>
  );
}