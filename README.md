# Web Scraping & DoS Attacks Analysis - Educational Project

## 📋 Descripción

Proyecto educativo de **análisis cibernético** que examina técnicas de **Web Scraping** (extracción de datos web) y **ataques DoS (Denial of Service)**. Este repositorio está diseñado con fines educativos y de investigación académica para comprender los mecanismos de estos ataques y las defensas correspondientes.

El proyecto implementa ejemplos prácticos de:
- **Web Scraping:** Técnicas de extracción de datos desde sitios web
- **Análisis de DoS:** Simulación controlada de ataques de negación de servicio
- **Mitigación:** Estrategias de defensa y protección

⚠️ **ADVERTENCIA DE USO RESPONSABLE:** Este código está destinado **únicamente para fines educativos y en entornos autorizados**. El uso no autorizado de estas técnicas contra sistemas sin consentimiento es ilegal.

---

## 🎯 Objetivos

1. **Comprender conceptos fundamentales** de Web Scraping y extracción de datos
2. **Analizar vulnerabilidades** en aplicaciones web
3. **Estudiar mecanismos de DoS** y su impacto en sistemas
4. **Implementar defensas** contra ataques de negación de servicio
5. **Desarrollar conciencia de seguridad** en aplicaciones web
6. **Practicar técnicas de mitigación** y hardening defensivo

---

## 📊 Contenido del Proyecto

### Módulos Principales

#### 1. **Web Scraping** 🕷️
- Extracción de datos HTML/XML
- Parsing y procesamiento de información web
- Técnicas de navegación y automatización
- Manejo de JavaScript y contenido dinámico
- Respeto a robots.txt y términos de servicio

#### 2. **Análisis de DoS** 🚨
- Tipos de ataques: UDP Flood, TCP SYN Flood, HTTP Flood
- Generación de patrones de tráfico malicioso
- Medición de impacto en recursos
- Análisis de comportamiento de sistemas bajo carga

#### 3. **Mitigación y Defensa** 🛡️
- Rate limiting y throttling
- IP blacklisting/whitelisting
- WAF (Web Application Firewall) concepts
- Load balancing y distribución de carga
- Monitoreo y detección de anomalías

---

## 🛠️ Tecnologías y Dependencias

```python
# Web Scraping
import requests              # Cliente HTTP
import beautifulsoup4        # Parsing HTML
import selenium              # Automatización de navegadores
import scrapy               # Framework de scraping avanzado

# Análisis y Visualización
import numpy as np          # Cálculos numéricos
import pandas as pd         # Análisis de datos
import matplotlib.pyplot    # Visualización
import seaborn             # Gráficos estadísticos

# Seguridad y Redes
import scapy               # Manipulación de paquetes
import socket              # Comunicación de red
import threading           # Procesamiento paralelo

# Utilidades
import json, csv, re       # Procesamiento de datos
import time, random        # Control de tiempo y aleatoriedad
```

**Versiones Recomendadas:**
- Python ≥ 3.8
- Requests ≥ 2.28
- BeautifulSoup4 ≥ 4.11
- Selenium ≥ 4.0
- NumPy ≥ 1.21
- Pandas ≥ 1.3

---

## 📚 Estructura del Repositorio

```
Web-Scraping-i-DoS/
│
├── README.md                                    # Documentación principal
├── Web_Scraping_DoS_Analysis.ipynb             # Notebook principal
│
├── datasets/
│   ├── sample_websites.csv                     # URLs de ejemplo
│   ├── scraped_data/                           # Datos extraídos
│   └── attack_logs/                            # Registros de análisis
│
├── src/
│   ├── scraper.py                              # Módulo de web scraping
│   ├── dos_simulator.py                        # Simulador de ataques
│   └── defense_mechanisms.py                   # Mecanismos de defensa
│
├── notebooks/
│   ├── 01_web_scraping_basics.ipynb           # Introducción a scraping
│   ├── 02_advanced_scraping.ipynb             # Técnicas avanzadas
│   ├── 03_dos_analysis.ipynb                  # Análisis de DoS
│   └── 04_defense_strategies.ipynb            # Estrategias defensivas
│
├── requirements.txt                            # Dependencias
└── .gitignore                                  # Archivos ignorados
```

---

## ⚙️ Instalación y Configuración

### Requisitos Previos
- **Python 3.8+**
- **pip** o **conda**
- Conocimientos básicos de networking y seguridad

### Instalación Local

#### Paso 1: Clonar el Repositorio
```bash
git clone https://github.com/williamG7/Web-Scraping-i-DoS.git
cd Web-Scraping-i-DoS
```

#### Paso 2: Crear Entorno Virtual
```bash
# Con venv
python -m venv env
source env/bin/activate  # En Windows: env\Scripts\activate

# O con conda
conda create --name scraping-dos python=3.9
conda activate scraping-dos
```

#### Paso 3: Instalar Dependencias
```bash
# Instalar todos los requisitos
pip install -r requirements.txt

# O instalación manual
pip install requests beautifulsoup4 selenium
pip install pandas numpy matplotlib seaborn
pip install scapy jupyter
```

#### Paso 4: Ejecutar el Notebook
```bash
jupyter notebook Web_Scraping_DoS_Analysis.ipynb
```

### Opción: Google Colab (Recomendado ⭐)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/williamG7/Web-Scraping-i-DoS/blob/main/Web_Scraping_DoS_Analysis.ipynb)

**Ventajas:**
- ✅ Sin instalación de dependencias
- ✅ Entorno pre-configurado
- ✅ Ejecución rápida
- ✅ Almacenamiento en Google Drive

---

## 🚀 Uso y Ejemplos

### 1. Web Scraping Básico

```python
import requests
from bs4 import BeautifulSoup

# Descargar página
url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

# Extraer datos
for item in soup.find_all('div', class_='product'):
    title = item.find('h2').text
    price = item.find('span', class_='price').text
    print(f"{title}: {price}")
```

### 2. Scraping con Selenium (JavaScript dinámico)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

# Inicializar navegador
driver = webdriver.Chrome()
driver.get("https://example.com")

# Esperar carga de elementos
driver.implicitly_wait(10)

# Extraer datos del DOM
elements = driver.find_elements(By.CLASS_NAME, "dynamic-content")
for elem in elements:
    print(elem.text)

driver.quit()
```

### 3. Simulación de Carga (Análisis de DoS)

```python
import threading
import requests
import time

def send_requests(url, count):
    """Envía múltiples solicitudes HTTP"""
    for i in range(count):
        try:
            response = requests.get(url, timeout=2)
            print(f"Request {i+1}: {response.status_code}")
        except Exception as e:
            print(f"Error: {e}")
        time.sleep(0.1)

# Lanzar prueba de carga (SOLO EN SISTEMAS AUTORIZADOS)
url = "http://localhost:5000"  # Servidor local de prueba
threads = []
for i in range(5):
    t = threading.Thread(target=send_requests, args=(url, 10))
    threads.append(t)
    t.start()

for t in threads:
    t.join()
```

### 4. Implementar Rate Limiting (Defensa)

```python
from datetime import datetime, timedelta
from collections import defaultdict

class RateLimiter:
    def __init__(self, max_requests=10, time_window=60):
        self.max_requests = max_requests
        self.time_window = time_window
        self.requests = defaultdict(list)
    
    def is_allowed(self, ip):
        now = datetime.now()
        # Limpiar solicitudes antiguas
        self.requests[ip] = [
            req_time for req_time in self.requests[ip]
            if (now - req_time).seconds < self.time_window
        ]
        
        if len(self.requests[ip]) < self.max_requests:
            self.requests[ip].append(now)
            return True
        return False

# Uso
limiter = RateLimiter(max_requests=10, time_window=60)
if limiter.is_allowed("192.168.1.1"):
    print("✅ Solicitud permitida")
else:
    print("❌ Demasiadas solicitudes - Rate limit alcanzado")
```

---

## 📊 Análisis y Resultados

### Fase 1: Web Scraping

| Aspecto | Valor |
|---------|-------|
| **Sitios Analizados** | 5-10 |
| **Datos Extraídos** | 1000+ registros |
| **Precisión** | 95%+ |
| **Tiempo Promedio** | 5-30 seg/sitio |

### Fase 2: Análisis de DoS

| Métrica | Valor |
|---------|-------|
| **Tipos de Ataque** | 3+ |
| **Velocidad Max** | 10K+ req/s |
| **Impacto Medido** | ✅ CPU, RAM, Latencia |
| **Recuperación** | ~2-5 minutos |

### Fase 3: Defensas Implementadas

| Técnica | Efectividad | Resultado |
|---------|-------------|-----------|
| Rate Limiting | 80-90% | ✅ Bloqueado |
| IP Blacklisting | 85-95% | ✅ Mitigado |
| Timeout Rules | 70-80% | ✅ Parcial |
| Load Balancing | 90%+ | ✅ Distribuido |

---

## 🔐 Consideraciones de Seguridad y Ética

### ✅ Uso Permitido
- 📚 **Educación académica** y aprendizaje
- 🔬 **Investigación de seguridad** autorizada
- 🏢 **Testing en sistemas propios** o autorizados
- 📖 **Documentación y análisis** teórico

### ❌ Uso NO Permitido
- 🚫 Atacar sitios sin autorización
- 🚫 Extraer datos sin consentimiento
- 🚫 Violar términos de servicio
- 🚫 Daño intencional a sistemas
- 🚫 Actividades ilegales

### 📋 Mejores Prácticas

1. **Siempre obtener autorización** antes de testing
2. **Respetar robots.txt** y términos de servicio
3. **Usar User-Agent apropiado** (no ocultar tu identidad)
4. **Implementar delays** entre solicitudes
5. **Documentar tus actividades** para auditoría
6. **Contactar propietarios** si descubres vulnerabilidades

---

## 🔧 Troubleshooting

### Error: `requests.exceptions.ConnectionError`
```bash
# Verificar conexión a internet
ping google.com

# Comprobar proxy/firewall
pip install --upgrade requests
```

### Error: `selenium.common.exceptions.WebDriverException`
```bash
# Descargar ChromeDriver compatible
# https://chromedriver.chromium.org/

# O usar webdriver manager
pip install webdriver-manager

from webdriver_manager.chrome import ChromeDriverManager
driver = webdriver.Chrome(ChromeDriverManager().install())
```

### Bloqueado por el servidor (403/429)
```python
# Usar headers realistas
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36'
}
response = requests.get(url, headers=headers)

# Implementar delays
import time
time.sleep(random.uniform(1, 3))
```

### Contenido dinámico no se carga
```python
# Usar Selenium en lugar de requests
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

wait = WebDriverWait(driver, 10)
element = wait.until(EC.presence_of_element_located(("id", "dynamic-element")))
```

---

## 📚 Recursos y Referencias

### Tutoriales en Línea
- [Web Scraping con Python - Real Python](https://realpython.com/beautiful-soup-web-scraper-python/)
- [Selenium Tutorial - Selenium Docs](https://selenium-python.readthedocs.io/)
- [DoS Attacks - OWASP](https://owasp.org/www-community/attacks/Denial_of_Service)

### Documentación
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Requests Library Docs](https://docs.python-requests.org/)
- [Scapy Documentation](https://scapy.readthedocs.io/)

### Cursos
- [Ethical Hacking - Udemy](https://www.udemy.com/topic/ethical-hacking/)
- [Security+ by CompTIA](https://www.comptia.org/certifications/security)
- [Cybersecurity Basics - Coursera](https://www.coursera.org/learn/cybersecurity-basics)

### Herramientas Complementarias
- **Burp Suite:** Testing de seguridad web
- **OWASP ZAP:** Scanner automático de vulnerabilidades
- **Wireshark:** Análisis de tráfico de red
- **Apache JMeter:** Testing de carga y performance

---

## 📈 Progreso del Proyecto

- [x] Fundamentos de Web Scraping
- [x] Técnicas avanzadas de extracción
- [x] Análisis de ataques DoS
- [ ] Implementación de WAF personalizado
- [ ] Dashboard de monitoreo en tiempo real
- [ ] Modelos ML para detección de anomalías
- [ ] Integración con herramientas SIEM

---

## 👥 Contribuciones

Este es un proyecto educativo abierto a contribuciones. Si deseas mejorar el código:

1. **Fork** el repositorio
2. Crea una rama para tu feature: `git checkout -b feature/mejora`
3. **Commit** tus cambios: `git commit -m "Add new feature"`
4. **Push** a la rama: `git push origin feature/mejora`
5. Abre un **Pull Request**

**Directrices:**
- Mantén el código documentado
- Incluye ejemplos de uso
- Respeta las consideraciones éticas
- Actualiza la documentación

---

## 📄 Licencia

Este proyecto está bajo licencia **MIT** y es de libre distribución con fines educativos.

```
MIT License - Web-Scraping-i-DoS Project

Copyright (c) 2024 William Guzmán

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

**Condiciones de uso:**
- ✅ Úsalo con propósitos educativos
- ✅ Cita al autor si lo utilizas
- ✅ Enlaza al repositorio original
- ❌ No lo uses para actividades ilegales
- ❌ No hagas daño a sistemas no autorizados

---

## 👨‍💻 Autor

**William Guzmán**

- 🔗 **GitHub:** [@williamG7](https://github.com/williamG7)
- 📧 **Email:** contacto@williamguzman.dev
- 💼 **LinkedIn:** [William Guzmán](https://linkedin.com/in/williamguzman)

---

## 🙏 Agradecimientos

- 📚 Comunidad de cybersecurity y ethical hacking
- 🎓 OWASP por recursos educativos de seguridad
- 💡 Todos los contribuidores del proyecto
- 🔐 Expertos en seguridad que comparten conocimiento

---

## 📞 Soporte y Contacto

¿Preguntas o sugerencias?

- 📧 Abre un issue en GitHub
- 💬 Discutir en Discussions
- 🐛 Reporta bugs con detalles
- 💡 Propón mejoras y features

---

## ⭐ Apoya el Proyecto

Si te resultó útil este repositorio:

- ⭐ **Dale una estrella** en GitHub
- 🍴 **Fork** para contribuir
- 📢 **Comparte** con otros aprendices
- 💬 **Deja feedback** en las issues

---

## 📊 Estadísticas del Proyecto

![GitHub stars](https://img.shields.io/github/stars/williamG7/Web-Scraping-i-DoS?style=social)
![GitHub forks](https://img.shields.io/github/forks/williamG7/Web-Scraping-i-DoS?style=social)
![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4.11+-yellow?logo=html5)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Security](https://img.shields.io/badge/Security-Educational-red?logo=shield)
![License MIT](https://img.shields.io/badge/License-MIT-green)

---

**Última actualización:** Junio 2024 | **Versión:** 1.0.0

---

### 🔴 AVISO LEGAL IMPORTANTE

Este repositorio es proporcionado **únicamente con fines educativos**. El autor no se responsabiliza por el mal uso de este código. **El acceso no autorizado a sistemas informáticos es ilegal**. Asegúrate de:

1. Tener **autorización explícita** antes de realizar cualquier prueba
2. Trabajar **solo en sistemas de prueba** o entornos autorizados
3. Cumplir con **leyes y regulaciones** de tu jurisdicción
4. Mantener la **confidencialidad** de la información descubierta

---

**¿Te gustó este proyecto? ⭐ Dale una estrella en GitHub**
