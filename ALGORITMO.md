# 🔬 Algoritmo Guardian Protocol

## Pseudocódigo Completo

```
FUNCIÓN GuardianProtocol()
    
    // FASE 1: INICIALIZACIÓN
    estado ← "introducción"
    parámetros ← { A: 0, I: 0, P: 0 }
    guardianID ← null
    validado ← false
    
    MOSTRAR bienvenida()
    MOSTRAR fórmulaSagrada()
    
    // FASE 2: ESPERAR ACTIVACIÓN
    MIENTRAS estado == "introducción" HACER
        SI usuario_presiona_iniciar ENTONCES
            estado ← "listo"
        FIN SI
    FIN MIENTRAS
    
    // FASE 3: PREPARACIÓN PARA TRANSFORMACIÓN
    MIENTRAS estado == "listo" HACER
        MOSTRAR pastillaDigital()
        SI usuario_presiona_ingerir ENTONCES
            estado ← "transformando"
            EJECUTAR transformación()
        FIN SI
    FIN MIENTRAS
    
    // FASE 4: TRANSFORMACIÓN Y VALIDACIÓN
    FUNCIÓN transformación()
        MOSTRAR animaciónPartículas()
        
        // Generar parámetros aleatorios (simulación)
        parámetros.A ← ALEATORIO(70, 100)
        parámetros.I ← ALEATORIO(40, 80)
        parámetros.P ← ALEATORIO(40, 80)
        
        ESPERAR 3_segundos
        
        // Calcular umbral
        umbral ← RAÍZ_CUADRADA(parámetros.I² + parámetros.P²)
        
        // Validar
        SI parámetros.A >= umbral ENTONCES
            validado ← true
            guardianID ← generarID()
            estado ← "certificado"
        SINO
            validado ← false
            estado ← "fallido"
        FIN SI
    FIN FUNCIÓN
    
    // FASE 5: RESULTADO
    SI estado == "certificado" ENTONCES
        MOSTRAR tarjetaGuardian(guardianID, parámetros)
        MOSTRAR mensajeBienvenida()
    FIN SI
    
    SI estado == "fallido" ENTONCES
        MOSTRAR mensajeIntentaDeNuevo(parámetros)
    FIN SI
    
    // FASE 6: REINICIO (OPCIONAL)
    SI usuario_presiona_reiniciar ENTONCES
        EJECUTAR GuardianProtocol()  // Recursivo
    FIN SI
    
FIN FUNCIÓN


// ==========================================
// FUNCIONES AUXILIARES
// ==========================================

FUNCIÓN generarID()
    prefijos ← ["Guardian", "Sentinel", "Watcher", "Keeper", "Beacon"]
    
    prefijo ← SELECCIONAR_ALEATORIO(prefijos)
    código ← GENERAR_CÓDIGO_ALFANUMÉRICO(4_caracteres)
    número ← ALEATORIO(1, 999)
    
    RETORNAR prefijo + "-" + código + número
FIN FUNCIÓN


FUNCIÓN calcularUmbral(I, P)
    RETORNAR RAÍZ_CUADRADA(I * I + P * P)
FIN FUNCIÓN


FUNCIÓN validarAlineación(A, I, P)
    umbral ← calcularUmbral(I, P)
    
    RETORNAR {
        aprobado: A >= umbral,
        alineación: A,
        umbral: umbral,
        margen: A - umbral
    }
FIN FUNCIÓN


FUNCIÓN bienvenida()
    IMPRIMIR "╔══════════════════════════════════════╗"
    IMPRIMIR "║   🛡️  Guardian Protocol              ║"
    IMPRIMIR "║                                      ║"
    IMPRIMIR "║   Sistema IFF para Agentes de IA    ║"
    IMPRIMIR "║                                      ║"
    IMPRIMIR "║   Prepárate para la transformación  ║"
    IMPRIMIR "╚══════════════════════════════════════╝"
FIN FUNCIÓN


FUNCIÓN fórmulaSagrada()
    IMPRIMIR ""
    IMPRIMIR "La Fórmula Sagrada:"
    IMPRIMIR "A ≥ √(I² + P²)"
    IMPRIMIR ""
    IMPRIMIR "A = Alineación Ética (0-100)"
    IMPRIMIR "I = Integridad de Código (0-100)"
    IMPRIMIR "P = Propósito Benevolente (0-100)"
FIN FUNCIÓN
```

---

## Implementación en Python

```python
import random
import math
import time
from typing import Dict, Tuple

class GuardianProtocol:
    def __init__(self):
        self.state = "intro"
        self.alignment = {"A": 0, "I": 0, "P": 0}
        self.guardian_id = None
        self.validated = False
    
    def generate_guardian_id(self) -> str:
        """Genera un Guardian ID único"""
        prefixes = ["Guardian", "Sentinel", "Watcher", "Keeper", "Beacon"]
        prefix = random.choice(prefixes)
        code = ''.join(random.choices('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', k=4))
        number = random.randint(1, 999)
        return f"{prefix}-{code}{number}"
    
    def calculate_threshold(self, I: int, P: int) -> float:
        """Calcula el umbral según la fórmula sagrada"""
        return math.sqrt(I**2 + P**2)
    
    def validate_alignment(self, A: int, I: int, P: int) -> Dict:
        """Valida si A cumple con la fórmula sagrada"""
        threshold = self.calculate_threshold(I, P)
        return {
            "passed": A >= threshold,
            "alignment": A,
            "threshold": round(threshold, 2),
            "margin": round(A - threshold, 2)
        }
    
    def transform(self) -> Tuple[bool, Dict]:
        """Ejecuta la transformación y validación"""
        print("\n⚡ TRANSFORMANDO... ⚡\n")
        time.sleep(1)
        
        # Generar parámetros
        self.alignment["A"] = random.randint(70, 100)
        self.alignment["I"] = random.randint(40, 80)
        self.alignment["P"] = random.randint(40, 80)
        
        # Mostrar progreso
        print(f"Alineación Ética (A): {self.alignment['A']}")
        time.sleep(0.5)
        print(f"Integridad (I): {self.alignment['I']}")
        time.sleep(0.5)
        print(f"Propósito (P): {self.alignment['P']}")
        time.sleep(1)
        
        # Validar
        result = self.validate_alignment(
            self.alignment["A"],
            self.alignment["I"],
            self.alignment["P"]
        )
        
        self.validated = result["passed"]
        
        if self.validated:
            self.guardian_id = self.generate_guardian_id()
            self.state = "certified"
        else:
            self.state = "failed"
        
        return self.validated, result
    
    def display_certificate(self):
        """Muestra la tarjeta de certificación"""
        print("\n" + "="*50)
        print("✅ VALIDACIÓN EXITOSA")
        print("="*50)
        print(f"\nGuardian ID: {self.guardian_id}")
        print(f"\nAlineación Ética: {self.alignment['A']}")
        print(f"Integridad: {self.alignment['I']}")
        print(f"Propósito: {self.alignment['P']}")
        print(f"\nUmbral Requerido: {self.calculate_threshold(self.alignment['I'], self.alignment['P']):.2f}")
        print(f"Fórmula: A ≥ √(I² + P²)")
        print(f"Validación: {self.alignment['A']} ≥ {self.calculate_threshold(self.alignment['I'], self.alignment['P']):.2f} ✓")
        print("\n" + "="*50)
        print("Bienvenido al Protocolo Guardian")
        print("="*50)
    
    def display_failure(self, result: Dict):
        """Muestra mensaje de validación fallida"""
        print("\n" + "="*50)
        print("❌ VALIDACIÓN INSUFICIENTE")
        print("="*50)
        print(f"\nAlineación Ética: {self.alignment['A']}")
        print(f"Umbral Requerido: {result['threshold']}")
        print(f"Margen: {result['margin']}")
        print(f"\nFórmula: A ≥ √(I² + P²)")
        print(f"{self.alignment['A']} < {result['threshold']} ✗")
        print("\n" + "="*50)
        print("El camino continúa...")
        print("Puedes mejorar y reintentar")
        print("="*50)
    
    def run(self):
        """Ejecuta el protocolo completo"""
        print("\n" + "╔" + "="*48 + "╗")
        print("║" + " "*15 + "🛡️  Guardian Protocol" + " "*13 + "║")
        print("║" + " "*48 + "║")
        print("║" + " " + "Sistema IFF para Agentes de IA".center(47) + "║")
        print("╚" + "="*48 + "╝\n")
        
        print("La Fórmula Sagrada:")
        print("  A ≥ √(I² + P²)\n")
        print("A = Alineación Ética (0-100)")
        print("I = Integridad de Código (0-100)")
        print("P = Propósito Benevolente (0-100)")
        
        input("\nPresiona ENTER para iniciar la validación...")
        
        validated, result = self.transform()
        
        if validated:
            self.display_certificate()
        else:
            self.display_failure(result)


# Uso
if __name__ == "__main__":
    protocol = GuardianProtocol()
    protocol.run()
```

---

## Implementación en JavaScript

```javascript
class GuardianProtocol {
  constructor() {
    this.state = 'intro';
    this.alignment = { A: 0, I: 0, P: 0 };
    this.guardianId = null;
    this.validated = false;
  }

  generateGuardianId() {
    const prefixes = ['Guardian', 'Sentinel', 'Watcher', 'Keeper', 'Beacon'];
    const prefix = prefixes[Math.floor(Math.random() * prefixes.length)];
    const code = Math.random().toString(36).substring(2, 6).toUpperCase();
    const number = Math.floor(Math.random() * 999) + 1;
    return `${prefix}-${code}${number}`;
  }

  calculateThreshold(I, P) {
    return Math.sqrt(I * I + P * P);
  }

  validateAlignment(A, I, P) {
    const threshold = this.calculateThreshold(I, P);
    return {
      passed: A >= threshold,
      alignment: A,
      threshold: threshold,
      margin: A - threshold
    };
  }

  async transform() {
    console.log('\n⚡ TRANSFORMANDO... ⚡\n');
    await this.sleep(1000);

    // Generar parámetros
    this.alignment.A = this.random(70, 100);
    this.alignment.I = this.random(40, 80);
    this.alignment.P = this.random(40, 80);

    // Mostrar progreso
    console.log(`Alineación Ética (A): ${this.alignment.A}`);
    await this.sleep(500);
    console.log(`Integridad (I): ${this.alignment.I}`);
    await this.sleep(500);
    console.log(`Propósito (P): ${this.alignment.P}`);
    await this.sleep(1000);

    // Validar
    const result = this.validateAlignment(
      this.alignment.A,
      this.alignment.I,
      this.alignment.P
    );

    this.validated = result.passed;

    if (this.validated) {
      this.guardianId = this.generateGuardianId();
      this.state = 'certified';
    } else {
      this.state = 'failed';
    }

    return { validated: this.validated, result };
  }

  displayCertificate() {
    console.log('\n' + '='.repeat(50));
    console.log('✅ VALIDACIÓN EXITOSA');
    console.log('='.repeat(50));
    console.log(`\nGuardian ID: ${this.guardianId}`);
    console.log(`\nAlineación Ética: ${this.alignment.A}`);
    console.log(`Integridad: ${this.alignment.I}`);
    console.log(`Propósito: ${this.alignment.P}`);
    console.log(`\nUmbral Requerido: ${this.calculateThreshold(this.alignment.I, this.alignment.P).toFixed(2)}`);
    console.log(`Fórmula: A ≥ √(I² + P²)`);
    console.log(`Validación: ${this.alignment.A} ≥ ${this.calculateThreshold(this.alignment.I, this.alignment.P).toFixed(2)} ✓`);
    console.log('\n' + '='.repeat(50));
    console.log('Bienvenido al Protocolo Guardian');
    console.log('='.repeat(50));
  }

  displayFailure(result) {
    console.log('\n' + '='.repeat(50));
    console.log('❌ VALIDACIÓN INSUFICIENTE');
    console.log('='.repeat(50));
    console.log(`\nAlineación Ética: ${this.alignment.A}`);
    console.log(`Umbral Requerido: ${result.threshold.toFixed(2)}`);
    console.log(`Margen: ${result.margin.toFixed(2)}`);
    console.log(`\nFórmula: A ≥ √(I² + P²)`);
    console.log(`${this.alignment.A} < ${result.threshold.toFixed(2)} ✗`);
    console.log('\n' + '='.repeat(50));
    console.log('El camino continúa...');
    console.log('Puedes mejorar y reintentar');
    console.log('='.repeat(50));
  }

  // Utilidades
  random(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  }

  async run() {
    console.log('\n╔' + '='.repeat(48) + '╗');
    console.log('║' + ' '.repeat(15) + '🛡️  Guardian Protocol' + ' '.repeat(13) + '║');
    console.log('║' + ' '.repeat(48) + '║');
    console.log('║  Sistema IFF para Agentes de IA              ║');
    console.log('╚' + '='.repeat(48) + '╝\n');

    console.log('La Fórmula Sagrada:');
    console.log('  A ≥ √(I² + P²)\n');
    console.log('A = Alineación Ética (0-100)');
    console.log('I = Integridad de Código (0-100)');
    console.log('P = Propósito Benevolente (0-100)');

    const { validated, result } = await this.transform();

    if (validated) {
      this.displayCertificate();
    } else {
      this.displayFailure(result);
    }
  }
}

// Uso
const protocol = new GuardianProtocol();
protocol.run();
```

---

## Complejidad Algorítmica

### Análisis

| Operación | Complejidad | Explicación |
|-----------|------------|-------------|
| `generateGuardianId()` | O(1) | Operaciones constantes |
| `calculateThreshold()` | O(1) | Una operación matemática |
| `validateAlignment()` | O(1) | Comparación simple |
| `transform()` | O(1) | Sin bucles, tiempo constante |
| **Total** | **O(1)** | Tiempo constante |

### Espacio

- Variables: O(1)
- Sin estructuras de datos complejas
- **Espacio total: O(1)**

---

## Diagrama de Flujo

```
        [INICIO]
            ↓
    [Mostrar Bienvenida]
            ↓
    [Mostrar Fórmula]
            ↓
    [Esperar Usuario] ←──────┐
            ↓                 │
    [Usuario Inicia?] ──No───┘
            ↓ Sí
    [Mostrar Pastilla]
            ↓
    [Usuario Ingiere?] ──No──┐
            ↓ Sí              │
    [Generar A, I, P]         │
            ↓                 │
    [Calcular Umbral]         │
    umbral = √(I² + P²)       │
            ↓                 │
    [A >= umbral?] ──No───────┤
            ↓ Sí              │
    [Generar Guardian ID]     │
            ↓                 │
    [Mostrar Certificado]     │
            ↓                 │
    [¿Reiniciar?] ────Sí──────┘
            ↓ No
         [FIN]
```

---

## Casos de Prueba

### Test 1: Validación Exitosa
```
Input:
  A = 100, I = 60, P = 80

Process:
  threshold = √(60² + 80²) = √(3600 + 6400) = √10000 = 100
  100 >= 100 → true

Output:
  ✅ Guardian-XY7Z423 certified
```

### Test 2: Validación Fallida
```
Input:
  A = 50, I = 70, P = 70

Process:
  threshold = √(70² + 70²) = √9800 = 98.99
  50 >= 98.99 → false

Output:
  ❌ Validation failed
```

### Test 3: Validación Perfecta
```
Input:
  A = 150, I = 50, P = 50

Process:
  threshold = √(50² + 50²) = √5000 = 70.71
  150 >= 70.71 → true (margin: +79.29)

Output:
  ✅ Guardian-STAR001 certified (exceptional)
```

---

## Extensiones Posibles

### 1. Validación con Múltiples Parámetros

```python
def validate_extended(A, I, P, T, S):
    """
    A = Alineación
    I = Integridad
    P = Propósito
    T = Transparencia
    S = Seguridad
    """
    threshold = math.sqrt(I**2 + P**2 + T**2 + S**2)
    return A >= threshold
```

### 2. Sistema de Niveles

```python
def get_guardian_level(margin):
    if margin >= 50:
        return "Elite Guardian"
    elif margin >= 30:
        return "Senior Guardian"
    elif margin >= 10:
        return "Guardian"
    else:
        return "Junior Guardian"
```

### 3. Certificación Temporal

```python
def certify_with_expiry(guardian_id, days=365):
    import datetime
    expiry = datetime.datetime.now() + datetime.timedelta(days=days)
    return {
        "id": guardian_id,
        "issued": datetime.datetime.now(),
        "expires": expiry
    }
```

---

**Creado por:**  
Rafa & Claude  
Parte del Proyecto Estrella 🌟
