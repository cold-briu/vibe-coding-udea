# sandus

## Objetivo

Quiero instalar open claw

## Instalando Open Claw

### 1. Contexto

Se recomienda usar una máquina virtual en la nube (VPS) para correr Open Claw.

Se requiere instalar curl y node version manager (nvm) previamente.

#### Algunos Riesgos

- **Prompt injection:** Manipulación del agente mediante entradas no confiables para ejecutar acciones no autorizadas.
- **Gateway exposition:** Exposición de interfaces de control a redes públicas sin autenticación robusta.
- **Secrets exposition:** Filtración de claves API, tokens o credenciales almacenados sin cifrado.
- **Malicious skills:** Ejecución de complementos de terceros comprometidos o con código dañino.
- **Accidental data deletion:** Eliminación o sobreescritura irreversible de archivos críticos del sistema por fallos de lógica.

### 2. Instalación

#### 2.1 Instalar curl

```bash
# actualiza la lista de paquetes
sudo apt update

# instala curl
# la opcion -y confirma la instalacion automaticamente
sudo apt install curl -y

# verifica que curl se instalo correctamente
curl --version
```

#### 2.2 Instalar nvm

Descarga el script de instalación disponible en:
https://github.com/nvm-sh/nvm

```bash
# descarga e instala nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

Abre una nueva terminal y luego:

```bash
# verifica que nvm se instalo correctamente
nvm --version

# instala la ultima version de node LTS
nvm install --lts

# selecciona esa version por defecto
nvm use --lts

# verifica que node se instalo correctamente
node --version
```

#### 2.3 Instalar Open Claw

Usando el script disponible en:
https://openclaw.ai/

```bash
# descarga e instala open claw
curl -fsSL https://openclaw.ai/install.sh | bash
```

### 3. Configurando Open Claw

```bash
# inicia el asistente de configuracion si no se abrio automaticamente
openclaw onboard
```

#### 3.1 Acepta disclaimer y nombra el agente

En el asistente interactivo, confirma el aviso de seguridad y asigna un nombre al agente:

```text
? Do you accept the security risk and proceed? (y/N) › y
? What should we call your first agent? › bot-name
```

#### 3.2 Agrega tus llaves API de IA

Selecciona tu proveedor (Anthropic, OpenAI, OpenRouter, etc.) e introduce tu clave API:

```text
? Select AI model provider: Anthropic
? Enter API key: ************************************
```

#### 3.3 Prueba el agente

```bash
# detiene el gateway y prueba el chat
openclaw gateway stop
openclaw chat
```

### 4. Configurando Telegram

#### 4.1 Habla con BotFather

https://telegram.me/BotFather

#### 4.2 Crea un nuevo bot

- Escribe `/newbot`
- Selecciona un nombre
- Copia el API token

#### 4.3 Configura el bot en Open Claw

```bash
# agrega el canal de telegram
openclaw channels add telegram
```

#### 4.4 Prueba e inicia

```bash
# prueba el canal y arranca open claw
openclaw channels test telegram
openclaw start
```