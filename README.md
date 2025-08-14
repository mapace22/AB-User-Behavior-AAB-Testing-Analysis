# proyecto_11_test_AAB
Startup de productos alimenticios | Comportamiento del usuario mediante embudo de ventas | Impacto de cambio con test A/A/B | Homogeneidad

# ANÁLISIS DE COMPORTAMIENTO DE USUARIO Y TEST A/A/B

## RESUMEN DEL PROYECTO
El proyecto analiza el comportamiento de usuarios en una aplicación de venta de productos alimenticios mediante:
1. Estudio del embudo de conversión para identificar puntos críticos
2. Evaluación de un cambio de diseño (fuentes) mediante test A/A/B
3. Análisis estadístico para determinar impacto en métricas clave

## OBJETIVO
1. Comprender el flujo de usuarios a través del embudo de ventas
2. Determinar si el cambio de fuentes afecta significativamente la conversión
3. Proporcionar recomendaciones basadas en datos para optimizar la experiencia del usuario

## METODOLOGÍA DE ANÁLISIS

### 1. DESCRIPCIÓN DE LOS DATOS
- **Dataset:** logs_exp_us.csv (244,126 registros)
- **Variables clave:**
  - EventName: Acciones del usuario (5 tipos)
  - DeviceIDHash: Identificador único de usuario
  - EventTimestamp: Marca temporal del evento
  - ExpId: Grupo experimental (246, 247 = control, 248 = tratamiento)

### 2. PREPROCESAMIENTO DE DATOS
- Renombrado de columnas para mayor claridad
- Conversión de timestamp a formato datetime
- Filtrado de periodo incompleto (1.16% de eventos)
- Verificación de grupos experimentales:
  - Grupo 246: 2,484 usuarios
  - Grupo 247: 2,513 usuarios
  - Grupo 248: 2,537 usuarios

### 3. PRUEBA DE HIPÓTESIS
#### 3.1 Análisis del Embudo
**Secuencia identificada:**
1. MainScreenAppear (98.47% usuarios)
2. OffersScreenAppear (60.96%)
3. CartScreenAppear (49.56%)
4. PaymentScreenSuccessful (46.97%)

**Hallazgos clave:**
- Mayor pérdida: Main → Offers (38.09% de usuarios)
- 47.7% completan todo el flujo

#### 3.2 Test A/A (Validación grupos control)
| Evento               | P-valor | Conclusión |
|----------------------|---------|------------|
| MainScreenAppear     | 0.7571  | Sin diferencia |
| OffersScreenAppear   | 0.2481  | Sin diferencia |
| CartScreenAppear     | 0.2288  | Sin diferencia |
| PaymentScreenSuccess | 0.1146  | Sin diferencia |

#### 3.3 Test A/B (Control vs Tratamiento)
| Evento               | P-valor | Diferencia |
|----------------------|---------|------------|
| MainScreenAppear     | 0.2942  | No significativa |
| OffersScreenAppear   | 0.4343  | No significativa |
| CartScreenAppear     | 0.1818  | No significativa |
| PaymentScreenSuccess | 0.6004  | No significativa |

## CONCLUSIONES PRINCIPALES
1. **Embudo de conversión:**
   - La mayor oportunidad de mejora está en la transición pantalla principal → ofertas
   - Buen rendimiento en etapas finales (94.78% conversión carrito → pago)

2. **Test A/A/B:**
   - Los grupos de control son estadísticamente equivalentes
   - **No hay evidencia** de que el cambio de fuentes afecte las conversiones
   - La nueva fuente no muestra impacto (ni positivo ni negativo)

3. **Recomendaciones:**
   - No implementar el cambio de fuentes basado en estos resultados
   - Enfocar esfuerzos en mejorar la transición Main → Offers
   - Considerar otros elementos de diseño para optimización

## TECNOLOGÍAS UTILIZADAS
- **Python** (Análisis principal)
- **Pandas** (Procesamiento de datos)
- **Matplotlib/Seaborn** (Visualizaciones)
- **SciPy** (Pruebas estadísticas)
- **Statsmodels** (Pruebas de proporciones)
