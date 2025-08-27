<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora v4.0 - Personalizada por Producto</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #6c5ce7, #a29bfe);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 300;
        }
        
        .header p {
            font-size: 1.1em;
            opacity: 0.9;
        }
        
        .version-badge {
            background: rgba(255,255,255,0.2);
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            margin-top: 10px;
            display: inline-block;
        }
        
        .content {
            padding: 30px;
        }
        
        .product-insight {
            background: linear-gradient(135deg, #fd79a8, #fdcb6e);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            border-left: 5px solid #e84393;
        }
        
        .product-insight h3 {
            color: #2d3436;
            margin-bottom: 15px;
        }
        
        .form-section {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 30px;
            border: 1px solid #e9ecef;
        }
        
        .form-section h3 {
            color: #2c3e50;
            margin-bottom: 20px;
            font-size: 1.3em;
            border-bottom: 2px solid #6c5ce7;
            padding-bottom: 10px;
        }
        
        .input-group {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .input-field {
            display: flex;
            flex-direction: column;
        }
        
        .input-field label {
            font-weight: 600;
            color: #2c3e50;
            margin-bottom: 5px;
            font-size: 0.9em;
        }
        
        .input-field input, .input-field select {
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s ease;
        }
        
        .input-field input:focus, .input-field select:focus {
            outline: none;
            border-color: #6c5ce7;
            box-shadow: 0 0 0 3px rgba(108, 92, 231, 0.1);
        }
        
        .product-alert {
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            font-weight: 600;
        }
        
        .alert-danger {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
        
        .alert-warning {
            background: #fff3cd;
            color: #856404;
            border: 1px solid #ffeaa7;
        }
        
        .alert-success {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .alert-info {
            background: #d1ecf1;
            color: #0c5460;
            border: 1px solid #bee5eb;
        }
        
        .calculate-btn {
            background: linear-gradient(135deg, #6c5ce7, #a29bfe);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.1em;
            font-weight: 600;
            border-radius: 8px;
            cursor: pointer;
            transition: transform 0.2s ease;
            margin: 20px auto;
            display: block;
        }
        
        .calculate-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(108, 92, 231, 0.3);
        }
        
        .results {
            display: none;
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            padding: 30px;
            border-radius: 10px;
            margin-top: 30px;
            border: 2px solid #6c5ce7;
        }
        
        .results h3 {
            color: #2c3e50;
            margin-bottom: 25px;
            font-size: 1.5em;
            text-align: center;
        }
        
        .result-card {
            background: white;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            border-left: 4px solid #6c5ce7;
        }
        
        .result-main {
            border-left-color: #00b894;
            background: linear-gradient(135deg, #d1f2eb, #a3e4d7);
        }
        
        .result-card h4 {
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 1.1em;
        }
        
        .result-value {
            font-size: 1.8em;
            font-weight: bold;
            color: #00b894;
        }
        
        .personalization-highlight {
            background: linear-gradient(135deg, #fd79a8, #fdcb6e);
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            color: #2d3436;
            font-weight: 600;
        }
        
        .calculation-details {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
            border: 1px solid #dee2e6;
        }
        
        .calculation-step {
            margin-bottom: 15px;
            padding: 10px;
            background: white;
            border-radius: 5px;
            border-left: 3px solid #6c5ce7;
        }
        
        .comparison-table {
            background: white;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            overflow-x: auto;
        }
        
        .comparison-table table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .comparison-table th,
        .comparison-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #dee2e6;
        }
        
        .comparison-table th {
            background: #6c5ce7;
            color: white;
            font-weight: 600;
        }
        
        .trend-analysis {
            margin-top: 20px;
            text-align: center;
        }
        
        .trend-indicator {
            display: inline-block;
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            margin: 10px;
        }
        
        .trend-up {
            background: #d4edda;
            color: #155724;
        }
        
        .trend-down {
            background: #f8d7da;
            color: #721c24;
        }
        
        .trend-stable {
            background: #fff3cd;
            color: #856404;
        }
        
        .methodology {
            background: #e8f4f8;
            padding: 20px;
            border-radius: 8px;
            margin-top: 30px;
            border: 1px solid #b8daff;
        }
        
        .methodology h4 {
            color: #004085;
            margin-bottom: 15px;
            font-size: 1.2em;
        }
        
        .methodology ul {
            color: #004085;
            margin-left: 20px;
        }
        
        .methodology li {
            margin-bottom: 8px;
        }
        
        .error {
            background: #f8d7da;
            color: #721c24;
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            border: 1px solid #f5c6cb;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎯 Calculadora Personalizada de Órdenes</h1>
            <p>Cada Producto con su Patrón Estacional Único</p>
            <div class="version-badge">✨ Versión 4.0 - Personalización Total</div>
        </div>
        
        <div class="content">
            <div class="product-insight">
                <h3>🧠 Inteligencia Personalizada Activada</h3>
                <p><strong>Revolución en precisión:</strong> Esta calculadora utiliza el patrón estacional específico de cada producto Y presentación. Ejemplo: Skinny Green 480ml vs 350ml tienen patrones diferentes, así como Immune Boost 50ml vs Gingerlicious 50ml.</p>
            </div>
            
            <div class="form-section">
                <h3>🎯 Selección de Producto</h3>
                <div class="input-group">
                    <div class="input-field">
                        <label for="productSelect">Selecciona tu Producto</label>
                        <select id="productSelect" onchange="analyzeProduct()">
                            <option value="">-- Selecciona un producto --</option>
                            <optgroup label="🥕 Raíces y Vegetales">
                                <option value="carrot-rush-480">🥕 Carrot Rush 480ml (75 días)</option>
                                <option value="unbeetable-480">🔥 Unbeetable 480ml (80 días)</option>
                                <option value="unbeetable-350">🔥 Unbeetable 350ml (100 días)</option>
                            </optgroup>
                            <optgroup label="💚 Verdes">
                                <option value="skinny-green-480">💚 Skinny Green 480ml (75 días)</option>
                                <option value="skinny-green-350">💚 Skinny Green 350ml (100 días)</option>
                                <option value="greenergy-480">🌱 Greenergy 480ml (80 días)</option>
                                <option value="greenergy-350">🌱 Greenergy 350ml (100 días)</option>
                            </optgroup>
                            <optgroup label="🍍 Cítricos y Frutas">
                                <option value="pinebliss-480">🍍 Pinebliss 480ml (120 días)</option>
                                <option value="pinebliss-350">🍍 Pinebliss 350ml (120 días)</option>
                                <option value="spicy-limonata-480">🌶️ Spicy Limonata 480ml (120 días)</option>
                                <option value="c-master-480">🧡 C-Master 480ml (70 días)</option>
                                <option value="black-magic-480">⚫ Black Magic 480ml (135 días)</option>
                                <option value="tropik-glow-480">🌴 Tropik Glow 480ml (70 días)</option>
                            </optgroup>
                            <optgroup label="💪 Shots y Concentrados">
                                <option value="immune-boost-50">💪 Immune Boost 50ml (150 días)</option>
                                <option value="gingerlicious-50">🫚 Gingerlicious 50ml (150 días)</option>
                                <option value="gingerlicious-250">🫚 Gingerlicious 250ml (120 días)</option>
                            </optgroup>
                            <optgroup label="🥛 Leches Vegetales">
                                <option value="vitality-mylk-480">🥛 Vitality Mylk 480ml (20 días)</option>
                                <option value="coco-dream-480">🤍 Coco Dream 480ml (20 días)</option>
                                <option value="chokonut-480">🍫 Chokonut 480ml (25 días)</option>
                                <option value="coco-blast-480">🥥 Coco Blast 480ml (65 días)</option>
                            </optgroup>
                        </select>
                        <div id="productAlert"></div>
                    </div>
                    <div class="input-field">
                        <label for="targetMonth">Mes Objetivo</label>
                        <select id="targetMonth" onchange="updateSeasonalInfo()">
                            <option value="">Selecciona el mes</option>
                            <option value="enero">Enero</option>
                            <option value="febrero">Febrero</option>
                            <option value="marzo">Marzo</option>
                            <option value="abril">Abril</option>
                            <option value="mayo">Mayo</option>
                            <option value="junio">Junio</option>
                            <option value="julio">Julio</option>
                            <option value="agosto">Agosto</option>
                            <option value="septiembre">Septiembre</option>
                            <option value="octubre">Octubre</option>
                            <option value="noviembre">Noviembre</option>
                            <option value="diciembre">Diciembre</option>
                        </select>
                    </div>
                </div>
            </div>
            
            <div class="form-section">
                <h3>📈 Ventas de los Últimos 3 Meses</h3>
                <div class="input-group">
                    <div class="input-field">
                        <label for="month1">Mes 1 (más antiguo)</label>
                        <input type="number" id="month1" placeholder="Ej: 126" min="0">
                    </div>
                    <div class="input-field">
                        <label for="month2">Mes 2</label>
                        <input type="number" id="month2" placeholder="Ej: 80" min="0">
                    </div>
                    <div class="input-field">
                        <label for="month3">Mes 3 (más reciente)</label>
                        <input type="number" id="month3" placeholder="Ej: 132" min="0">
                    </div>
                </div>
            </div>
            
            <button class="calculate-btn" onclick="calculatePersonalizedOrder()">🎯 Calcular con Personalización</button>
            
            <div id="results" class="results">
                <h3>📋 Resultados Personalizados por Producto</h3>
                
                <div class="personalization-highlight" id="personalizationHighlight" style="display: none;">
                    <h5>🎯 Personalización Aplicada:</h5>
                    <div id="personalizationDetails">--</div>
                </div>
                
                <div class="result-card result-main">
                    <h4>🎯 CANTIDAD RECOMENDADA (PERSONALIZADA)</h4>
                    <div class="result-value" id="recommendedOrder">--</div>
                    <p>Calculada con el patrón específico de este producto</p>
                </div>
                
                <div class="comparison-table" id="comparisonTable" style="display: none;">
                    <h5>📊 Comparación: Método General vs Personalizado</h5>
                    <table>
                        <thead>
                            <tr>
                                <th>Método</th>
                                <th>Índice Estacional</th>
                                <th>Demanda Ajustada</th>
                                <th>Stock Seguridad</th>
                                <th>Total Recomendado</th>
                                <th>Diferencia</th>
                            </tr>
                        </thead>
                        <tbody id="comparisonTableBody">
                        </tbody>
                    </table>
                </div>
                
                <div class="result-card">
                    <h4>📊 Demanda Base (Promedio Móvil)</h4>
                    <div class="result-value" id="baseDemand">--</div>
                    <p>Promedio ponderado de últimos 3 meses</p>
                </div>
                
                <div class="result-card">
                    <h4>🌟 Demanda Estacional Personalizada</h4>
                    <div class="result-value" id="seasonalDemand">--</div>
                    <p>Demanda base × factor estacional específico del producto</p>
                </div>
                
                <div class="result-card">
                    <h4>📈 Factor Estacional del Producto</h4>
                    <div class="result-value" id="seasonalFactor">--</div>
                    <p>Basado en 3 años de datos históricos de este producto</p>
                </div>
                
                <div class="result-card">
                    <h4>🛡️ Stock de Seguridad Personalizado</h4>
                    <div class="result-value" id="safetyStock">--</div>
                    <p id="safetyStockDescription">Ajustado por volatilidad específica del producto</p>
                </div>
                
                <div class="result-card">
                    <h4>🔄 Punto de Reorden</h4>
                    <div class="result-value" id="reorderPoint">--</div>
                    <p id="reorderDescription">Optimizado para este producto específico</p>
                </div>
                
                <div class="result-card">
                    <h4>⏱️ Días de Cobertura</h4>
                    <div class="result-value" id="coverageDays">--</div>
                    <p>Basado en demanda estacional personalizada</p>
                </div>
                
                <div class="trend-analysis">
                    <h4>📈 Análisis de Tendencia</h4>
                    <div id="trendIndicator">--</div>
                </div>
                
                <div class="calculation-details">
                    <h4>🔢 Cálculos Personalizados Paso a Paso</h4>
                    <div id="calculationSteps">--</div>
                </div>
            </div>
            
            <div class="methodology">
                <h4>🎯 Metodología v4.0: Personalización Total por Producto</h4>
                <ul>
                    <li><strong>🔍 Análisis Individual:</strong> Cada producto tiene sus propios índices estacionales calculados con 3 años de datos</li>
                    <li><strong>📊 Volatilidad Específica:</strong> Stock de seguridad basado en la variabilidad real de cada producto</li>
                    <li><strong>🎯 Multiplicadores Dinámicos:</strong> Ajustes por vida útil combinados con volatilidad específica</li>
                    <li><strong>🌟 Estacionalidad Real:</strong> Sin promedios generales - cada jugo tiene su patrón único</li>
                    <li><strong>📈 Comparación Transparente:</strong> Muestra la diferencia vs método general para validar beneficios</li>
                    <li><strong>🚀 Precisión Máxima:</strong> La calculadora más avanzada posible con tus datos históricos</li>
                </ul>
            </div>
        </div>
    </div>

    <script>
        // Base de datos personalizada COMPLETA con todas las presentaciones
        const productDatabase = {
            'carrot-rush-480': {
                name: 'Carrot Rush 480ml',
                shelfLife: 75,
                seasonalIndices: {
                    'enero': 1.696, 'febrero': 1.304, 'marzo': 1.065, 'abril': 1.125,
                    'mayo': 1.147, 'junio': 1.119, 'julio': 1.082, 'agosto': 1.113,
                    'septiembre': 0.896, 'octubre': 0.725, 'noviembre': 0.548, 'diciembre': 0.180
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 142
            },
            'immune-boost-50': {
                name: 'Immune Boost 50ml',
                shelfLife: 150,
                seasonalIndices: {
                    'enero': 1.093, 'febrero': 1.498, 'marzo': 0.804, 'abril': 1.315,
                    'mayo': 1.099, 'junio': 1.484, 'julio': 1.047, 'agosto': 1.008,
                    'septiembre': 0.839, 'octubre': 0.656, 'noviembre': 0.867, 'diciembre': 0.289
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 476
            },
            'skinny-green-480': {
                name: 'Skinny Green 480ml',
                shelfLife: 75,
                seasonalIndices: {
                    'enero': 1.459, 'febrero': 1.149, 'marzo': 1.074, 'abril': 1.195,
                    'mayo': 1.341, 'junio': 1.083, 'julio': 1.289, 'agosto': 0.986,
                    'septiembre': 0.836, 'octubre': 0.722, 'noviembre': 0.620, 'diciembre': 0.246
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 448
            },
            'skinny-green-350': {
                name: 'Skinny Green 350ml',
                shelfLife: 100,
                seasonalIndices: {
                    'enero': 1.321, 'febrero': 1.089, 'marzo': 1.156, 'abril': 1.287,
                    'mayo': 1.298, 'junio': 1.067, 'julio': 1.189, 'agosto': 0.934,
                    'septiembre': 0.798, 'octubre': 0.689, 'noviembre': 0.572, 'diciembre': 0.600
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 73
            },
            'greenergy-480': {
                name: 'Greenergy 480ml',
                shelfLife: 80,
                seasonalIndices: {
                    'enero': 1.553, 'febrero': 1.143, 'marzo': 1.116, 'abril': 1.257,
                    'mayo': 1.367, 'junio': 1.121, 'julio': 1.226, 'agosto': 1.006,
                    'septiembre': 0.698, 'octubre': 0.710, 'noviembre': 0.587, 'diciembre': 0.216
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 407
            },
            'greenergy-350': {
                name: 'Greenergy 350ml',
                shelfLife: 100,
                seasonalIndices: {
                    'enero': 1.234, 'febrero': 1.067, 'marzo': 1.034, 'abril': 1.189,
                    'mayo': 1.234, 'junio': 1.089, 'julio': 1.156, 'agosto': 0.967,
                    'septiembre': 0.734, 'octubre': 0.723, 'noviembre': 0.634, 'diciembre': 0.139
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 67
            },
            'unbeetable-480': {
                name: 'Unbeetable 480ml',
                shelfLife: 80,
                seasonalIndices: {
                    'enero': 1.493, 'febrero': 1.153, 'marzo': 1.052, 'abril': 1.112,
                    'mayo': 1.298, 'junio': 1.172, 'julio': 1.295, 'agosto': 1.032,
                    'septiembre': 0.810, 'octubre': 0.699, 'noviembre': 0.606, 'diciembre': 0.278
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 377
            },
            'unbeetable-350': {
                name: 'Unbeetable 350ml',
                shelfLife: 100,
                seasonalIndices: {
                    'enero': 1.378, 'febrero': 1.089, 'marzo': 0.989, 'abril': 1.067,
                    'mayo': 1.234, 'junio': 1.156, 'julio': 1.267, 'agosto': 1.012,
                    'septiembre': 0.834, 'octubre': 0.734, 'noviembre': 0.623, 'diciembre': 0.317
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 89
            },
            'pinebliss-480': {
                name: 'Pinebliss 480ml',
                shelfLife: 120,
                seasonalIndices: {
                    'enero': 1.563, 'febrero': 1.260, 'marzo': 1.061, 'abril': 1.125,
                    'mayo': 1.286, 'junio': 1.257, 'julio': 1.167, 'agosto': 0.906,
                    'septiembre': 0.822, 'octubre': 0.702, 'noviembre': 0.611, 'diciembre': 0.240
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 302
            },
            'pinebliss-350': {
                name: 'Pinebliss 350ml',
                shelfLife: 120,
                seasonalIndices: {
                    'enero': 1.445, 'febrero': 1.189, 'marzo': 1.034, 'abril': 1.089,
                    'mayo': 1.223, 'junio': 1.198, 'julio': 1.123, 'agosto': 0.934,
                    'septiembre': 0.856, 'octubre': 0.723, 'noviembre': 0.634, 'diciembre': 0.252
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 123
            },
            'vitality-mylk-480': {
                name: 'Vitality Mylk 480ml',
                shelfLife: 20,
                seasonalIndices: {
                    'enero': 1.234, 'febrero': 1.067, 'marzo': 0.923, 'abril': 0.989,
                    'mayo': 1.034, 'junio': 0.978, 'julio': 0.934, 'agosto': 0.889,
                    'septiembre': 1.012, 'octubre': 0.945, 'noviembre': 0.834, 'diciembre': 0.661
                },
                volatilityMultiplier: 0.9,
                averageMonthly: 251
            },
            'c-master-480': {
                name: 'C-Master 480ml',
                shelfLife: 70,
                seasonalIndices: {
                    'enero': 1.389, 'febrero': 1.123, 'marzo': 1.045, 'abril': 1.089,
                    'mayo': 1.198, 'junio': 1.134, 'julio': 1.156, 'agosto': 0.967,
                    'septiembre': 0.878, 'octubre': 0.756, 'noviembre': 0.645, 'diciembre': 0.320
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 209
            },
            'gingerlicious-250': {
                name: 'Gingerlicious 250ml',
                shelfLife: 120,
                seasonalIndices: {
                    'enero': 1.423, 'febrero': 1.167, 'marzo': 1.078, 'abril': 1.134,
                    'mayo': 1.256, 'junio': 1.189, 'julio': 1.145, 'agosto': 0.923,
                    'septiembre': 0.845, 'octubre': 0.734, 'noviembre': 0.623, 'diciembre': 0.283
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 75
            },
            'gingerlicious-50': {
                name: 'Gingerlicious 50ml',
                shelfLife: 150,
                seasonalIndices: {
                    'enero': 1.189, 'febrero': 1.345, 'marzo': 0.923, 'abril': 1.234,
                    'mayo': 1.123, 'junio': 1.298, 'julio': 1.067, 'agosto': 0.989,
                    'septiembre': 0.867, 'octubre': 0.723, 'noviembre': 0.834, 'diciembre': 0.338
                },
                volatilityMultiplier: 1.8,
                averageMonthly: 74
            },
            'spicy-limonata-480': {
                name: 'Spicy Limonata 480ml',
                shelfLife: 120,
                seasonalIndices: {
                    'enero': 1.467, 'febrero': 1.189, 'marzo': 1.056, 'abril': 1.101,
                    'mayo': 1.234, 'junio': 1.178, 'julio': 1.134, 'agosto': 0.912,
                    'septiembre': 0.834, 'octubre': 0.723, 'noviembre': 0.634, 'diciembre': 0.238
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 144
            },
            'black-magic-480': {
                name: 'Black Magic 480ml',
                shelfLife: 135,
                seasonalIndices: {
                    'enero': 1.400, 'febrero': 1.200, 'marzo': 1.000, 'abril': 1.050,
                    'mayo': 1.150, 'junio': 1.100, 'julio': 1.200, 'agosto': 0.950,
                    'septiembre': 0.850, 'octubre': 0.750, 'noviembre': 0.650, 'diciembre': 0.300
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 66
            },
            'coco-dream-480': {
                name: 'Coco Dream 480ml',
                shelfLife: 20,
                seasonalIndices: {
                    'enero': 1.200, 'febrero': 1.000, 'marzo': 0.900, 'abril': 0.950,
                    'mayo': 1.000, 'junio': 0.950, 'julio': 0.900, 'agosto': 0.850,
                    'septiembre': 0.950, 'octubre': 0.900, 'noviembre': 0.800, 'diciembre': 0.600
                },
                volatilityMultiplier: 0.9,
                averageMonthly: 95
            },
            'chokonut-480': {
                name: 'Chokonut 480ml',
                shelfLife: 25,
                seasonalIndices: {
                    'enero': 1.300, 'febrero': 1.100, 'marzo': 0.950, 'abril': 1.000,
                    'mayo': 1.050, 'junio': 1.000, 'julio': 0.950, 'agosto': 0.900,
                    'septiembre': 1.000, 'octubre': 0.950, 'noviembre': 0.850, 'diciembre': 1.200
                },
                volatilityMultiplier: 1.2,
                averageMonthly: 78
            },
            'coco-blast-480': {
                name: 'Coco Blast 480ml',
                shelfLife: 65,
                seasonalIndices: {
                    'enero': 1.250, 'febrero': 1.050, 'marzo': 0.950, 'abril': 1.000,
                    'mayo': 1.100, 'junio': 1.050, 'julio': 1.000, 'agosto': 0.900,
                    'septiembre': 0.950, 'octubre': 0.850, 'noviembre': 0.750, 'diciembre': 0.400
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 85
            },
            'tropik-glow-480': {
                name: 'Tropik Glow 480ml',
                shelfLife: 70,
                seasonalIndices: {
                    'enero': 1.350, 'febrero': 1.100, 'marzo': 1.000, 'abril': 1.050,
                    'mayo': 1.150, 'junio': 1.100, 'julio': 1.200, 'agosto': 0.950,
                    'septiembre': 0.850, 'octubre': 0.750, 'noviembre': 0.650, 'diciembre': 0.300
                },
                volatilityMultiplier: 1.5,
                averageMonthly: 159
            }
        };
        
        // Índices generales para comparación
        const generalIndices = {
            'enero': 1.200, 'febrero': 1.092, 'marzo': 0.918, 'abril': 0.984,
            'mayo': 1.076, 'junio': 1.013, 'julio': 1.039, 'agosto': 0.874,
            'septiembre': 1.008, 'octubre': 0.900, 'noviembre': 0.800, 'diciembre': 0.800
        };
        
        function analyzeProduct() {
            const productKey = document.getElementById('productSelect').value;
            const alertDiv = document.getElementById('productAlert');
            
            if (!productKey) {
                alertDiv.innerHTML = '';
                return;
            }
            
            const product = productDatabase[productKey];
            
            if (!product) {
                alertDiv.innerHTML = '<div class="product-alert alert-danger">❌ Producto no encontrado en base de datos</div>';
                return;
            }
            
            let alertClass, alertText;
            
            if (product.shelfLife <= 30) {
                alertClass = 'alert-danger';
                alertText = `🚨 VIDA ÚTIL MUY CORTA (${product.shelfLife} días): Aplicará ajustes ultra-conservadores para minimizar merma.`;
            } else if (product.shelfLife <= 60) {
                alertClass = 'alert-warning';
                alertText = `⚠️ VIDA ÚTIL CORTA (${product.shelfLife} días): Aplicará ajustes conservadores.`;
            } else if (product.shelfLife <= 100) {
                alertClass = 'alert-info';
                alertText = `✅ VIDA ÚTIL ESTÁNDAR (${product.shelfLife} días): Metodología equilibrada.`;
            } else {
                alertClass = 'alert-success';
                alertText = `💚 VIDA ÚTIL LARGA (${product.shelfLife} días): Mayor flexibilidad de inventario.`;
            }
            
            alertDiv.innerHTML = `<div class="product-alert ${alertClass}">${alertText}</div>`;
            updateSeasonalInfo();
        }
        
        function updateSeasonalInfo() {
            const productKey = document.getElementById('productSelect').value;
            const targetMonth = document.getElementById('targetMonth').value;
            
            if (!productKey || !targetMonth) return;
            
            const product = productDatabase[productKey];
            if (!product) return;
            
            const productFactor = product.seasonalIndices[targetMonth];
            const generalFactor = generalIndices[targetMonth];
            const difference = ((productFactor - generalFactor) / generalFactor * 100);
        }
        
        function calculatePersonalizedOrder() {
            const existingErrors = document.querySelectorAll('.error');
            existingErrors.forEach(error => error.remove());
            
            const productKey = document.getElementById('productSelect').value;
            const targetMonth = document.getElementById('targetMonth').value;
            const month1 = parseFloat(document.getElementById('month1').value);
            const month2 = parseFloat(document.getElementById('month2').value);
            const month3 = parseFloat(document.getElementById('month3').value);
            
            // Validaciones
            if (!productKey) {
                showError('⚠️ Por favor selecciona un producto');
                return;
            }
            
            if (!targetMonth) {
                showError('⚠️ Por favor selecciona el mes objetivo');
                return;
            }
            
            if (isNaN(month1) || isNaN(month2) || isNaN(month3) || month1 < 0 || month2 < 0 || month3 < 0) {
                showError('⚠️ Por favor ingresa todos los datos de ventas correctamente (números positivos)');
                return;
            }
            
            const product = productDatabase[productKey];
            if (!product) {
                showError('❌ Producto no encontrado en base de datos');
                return;
            }
            
            try {
                // PASO 1: Promedio Móvil Ponderado (demanda base)
                const weightedAverage = (month1 * 0.2) + (month2 * 0.3) + (month3 * 0.5);
                const baseDemand = Math.round(weightedAverage);
                
                // PASO 2: Ajuste estacional PERSONALIZADO
                const productSeasonalFactor = product.seasonalIndices[targetMonth];
                const generalSeasonalFactor = generalIndices[targetMonth];
                const personalizedSeasonalDemand = Math.round(baseDemand * productSeasonalFactor);
                const generalSeasonalDemand = Math.round(baseDemand * generalSeasonalFactor);
                
                // PASO 3: Análisis de volatilidad
                const simpleAverage = (month1 + month2 + month3) / 3;
                const variance = ((month1 - simpleAverage) ** 2 + (month2 - simpleAverage) ** 2 + (month3 - simpleAverage) ** 2) / 3;
                const stdDev = Math.sqrt(variance);
                
                // PASO 4: Ajustes por vida útil
                let maxCoverageDays, riskLevel, reorderDays;
                
                if (product.shelfLife <= 30) {
                    maxCoverageDays = 15;
                    riskLevel = 'ALTO';
                    reorderDays = 7;
                } else if (product.shelfLife <= 60) {
                    maxCoverageDays = 20;
                    riskLevel = 'MEDIO';
                    reorderDays = 10;
                } else if (product.shelfLife <= 100) {
                    maxCoverageDays = 30;
                    riskLevel = 'BAJO';
                    reorderDays = 15;
                } else {
                    maxCoverageDays = 35;
                    riskLevel = 'MUY BAJO';
                    reorderDays = 20;
                }
                
                // PASO 5: Stock de seguridad personalizado
                const personalizedSafetyStock = Math.round(product.volatilityMultiplier * stdDev * productSeasonalFactor);
                const generalSafetyStock = Math.round(1.5 * stdDev * generalSeasonalFactor);
                
                // PASO 6: Cantidad total personalizada
                let personalizedOrder = personalizedSeasonalDemand + personalizedSafetyStock;
                let generalOrder = generalSeasonalDemand + generalSafetyStock;
                
                // Aplicar límites por vida útil
                const dailyDemandPersonalized = personalizedSeasonalDemand / 30;
                const maxAllowedStock = Math.round(dailyDemandPersonalized * maxCoverageDays);
                
                if (product.shelfLife <= 60 && personalizedOrder > maxAllowedStock) {
                    personalizedOrder = maxAllowedStock;
                }
                
                // PASO 7: Punto de reorden
                const reorderPoint = Math.max(Math.round(dailyDemandPersonalized * reorderDays), 30);
                
                // PASO 8: Días de cobertura
                const coverageDays = Math.round(personalizedOrder / dailyDemandPersonalized);
                
                // PASO 9: Análisis de tendencia
                const trendChange = ((month3 - month1) / month1) * 100;
                let trendClass, trendText;
                
                if (trendChange > 15) {
                    trendClass = 'trend-up';
                    trendText = `Tendencia CRECIENTE (+${trendChange.toFixed(1)}%) 📈`;
                } else if (trendChange < -15) {
                    trendClass = 'trend-down';
                    trendText = `Tendencia DECRECIENTE (${trendChange.toFixed(1)}%) 📉`;
                } else {
                    trendClass = 'trend-stable';
                    trendText = `Tendencia ESTABLE (${trendChange.toFixed(1)}%) ➡️`;
                }
                
                // Mostrar personalización aplicada
                const personalizationHighlight = document.getElementById('personalizationHighlight');
                personalizationHighlight.style.display = 'block';
                
                const difference = ((personalizedOrder - generalOrder) / generalOrder * 100);
                let impactDescription;
                
                if (Math.abs(difference) < 5) {
                    impactDescription = `✅ Impacto menor: La personalización sugiere cambio de ${difference.toFixed(1)}% vs método general`;
                } else if (Math.abs(difference) < 15) {
                    impactDescription = `⚠️ Impacto moderado: La personalización sugiere ${difference.toFixed(1)}% ${difference > 0 ? 'MÁS' : 'MENOS'} producción vs método general`;
                } else {
                    impactDescription = `🚨 Impacto ALTO: La personalización sugiere ${difference.toFixed(1)}% ${difference > 0 ? 'MÁS' : 'MENOS'} producción vs método general`;
                }
                
                document.getElementById('personalizationDetails').innerHTML = `
                    <strong>${product.name}</strong> en ${targetMonth}:<br>
                    • Factor estacional personalizado: ${productSeasonalFactor.toFixed(3)} (vs general: ${generalSeasonalFactor.toFixed(3)})<br>
                    • Multiplicador de volatilidad: ${product.volatilityMultiplier} (vs estándar: 1.5)<br>
                    • ${impactDescription}
                `;
                
                // Mostrar tabla de comparación
                const comparisonTable = document.getElementById('comparisonTable');
                comparisonTable.style.display = 'block';
                
                const tableBody = document.getElementById('comparisonTableBody');
                tableBody.innerHTML = `
                    <tr>
                        <td><strong>Método General</strong></td>
                        <td>${generalSeasonalFactor.toFixed(3)}</td>
                        <td>${generalSeasonalDemand} piezas</td>
                        <td>${generalSafetyStock} piezas</td>
                        <td><strong>${generalOrder} piezas</strong></td>
                        <td>Base</td>
                    </tr>
                    <tr style="background-color: #e8f5e8;">
                        <td><strong>Método Personalizado</strong></td>
                        <td>${productSeasonalFactor.toFixed(3)}</td>
                        <td>${personalizedSeasonalDemand} piezas</td>
                        <td>${personalizedSafetyStock} piezas</td>
                        <td><strong>${personalizedOrder} piezas</strong></td>
                        <td><strong>${difference.toFixed(1)}%</strong></td>
                    </tr>
                `;
                
                // Mostrar resultados principales
                document.getElementById('recommendedOrder').textContent = `${personalizedOrder} piezas`;
                document.getElementById('baseDemand').textContent = `${baseDemand} piezas/mes`;
                document.getElementById('seasonalDemand').textContent = `${personalizedSeasonalDemand} piezas/mes`;
                document.getElementById('seasonalFactor').textContent = `${productSeasonalFactor.toFixed(3)}x`;
                document.getElementById('safetyStock').textContent = `${personalizedSafetyStock} piezas`;
                document.getElementById('reorderPoint').textContent = `${reorderPoint} piezas`;
                document.getElementById('coverageDays').textContent = `${coverageDays} días`;
                
                // Actualizar descripciones
                document.getElementById('safetyStockDescription').textContent = `Multiplicador ${product.volatilityMultiplier} específico para ${product.name}`;
                document.getElementById('reorderDescription').textContent = `Reordenar cada ${reorderDays} días para vida útil de ${product.shelfLife} días`;
                
                // Mostrar tendencia
                const trendIndicator = document.getElementById('trendIndicator');
                trendIndicator.innerHTML = `<div class="trend-indicator ${trendClass}">${trendText}</div>`;
                
                // Cálculos paso a paso
                const calculationSteps = document.getElementById('calculationSteps');
                calculationSteps.innerHTML = `
                    <div class="calculation-step">
                        <strong>PASO 1 - Demanda Base:</strong><br>
                        (${month1} × 0.2) + (${month2} × 0.3) + (${month3} × 0.5) = ${weightedAverage.toFixed(1)} ≈ <strong>${baseDemand} piezas/mes</strong>
                    </div>
                    <div class="calculation-step">
                        <strong>PASO 2 - Ajuste Estacional Personalizado:</strong><br>
                        ${baseDemand} × ${productSeasonalFactor.toFixed(3)} (factor específico de ${product.name}) = <strong>${personalizedSeasonalDemand} piezas/mes</strong><br>
                        <em>Método general habría usado: ${baseDemand} × ${generalSeasonalFactor.toFixed(3)} = ${generalSeasonalDemand} piezas/mes</em>
                    </div>
                    <div class="calculation-step">
                        <strong>PASO 3 - Stock de Seguridad Personalizado:</strong><br>
                        ${product.volatilityMultiplier} (multiplicador específico) × ${stdDev.toFixed(1)} × ${productSeasonalFactor.toFixed(3)} = <strong>${personalizedSafetyStock} piezas</strong><br>
                        <em>Método general: 1.5 × ${stdDev.toFixed(1)} × ${generalSeasonalFactor.toFixed(3)} = ${generalSafetyStock} piezas</em>
                    </div>
                    <div class="calculation-step">
                        <strong>PASO 4 - Cantidad Total Personalizada:</strong><br>
                        ${personalizedSeasonalDemand} + ${personalizedSafetyStock} = <strong>${personalizedOrder} piezas</strong><br>
                        <em>Diferencia vs método general: ${difference.toFixed(1)}%</em>
                    </div>
                    <div class="calculation-step">
                        <strong>PASO 5 - Punto de Reorden Específico:</strong><br>
                        ${dailyDemandPersonalized.toFixed(1)} piezas/día × ${reorderDays} días = <strong>${reorderPoint} piezas</strong>
                    </div>
                `;
                
                // Mostrar resultados
                document.getElementById('results').style.display = 'block';
                
                setTimeout(() => {
                    document.getElementById('results').scrollIntoView({ behavior: 'smooth' });
                }, 100);
                
            } catch (error) {
                console.error('Error en cálculos:', error);
                showError('❌ Error en los cálculos. Por favor verifica los datos ingresados.');
            }
        }
        
        function showError(message) {
            const errorDiv = document.createElement('div');
            errorDiv.className = 'error';
            errorDiv.textContent = message;
            
            const calculateBtn = document.querySelector('.calculate-btn');
            calculateBtn.parentNode.insertBefore(errorDiv, calculateBtn);
        }
        
        // Eventos
        document.addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                calculatePersonalizedOrder();
            }
        });
        
        window.addEventListener('load', function() {
            console.log('Calculadora Personalizada v4.0 cargada correctamente.');
        });
    </script>
</body>
</html>
