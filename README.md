# C2000™ DriverLib Reference Guide

<div align="center">

[![TI C2000](https://img.shields.io/badge/Target-TI%20C2000%E2%84%A2%20MCUs-red?style=for-the-badge&logo=texasinstruments)](https://www.ti.com/microcontrollers-mcus-processors/c2000-real-time-control-mcus/overview.html)
[![DriverLib](https://img.shields.io/badge/Library-C2000Ware%20DriverLib-blue?style=for-the-badge)](https://www.ti.com/tool/C2000WARE)
[![Language](https://img.shields.io/badge/Language-C%20%2F%20C%2B%2B-green?style=for-the-badge&logo=c)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Documentation](https://img.shields.io/badge/Docs-PT--BR%20%7C%20EN-orange?style=for-the-badge)](#-módulos-e-documentação)
[![Status](https://img.shields.io/badge/Status-Active%20Reference-brightgreen?style=for-the-badge)](#-roadmap-de-periféricos)

**Guia de Referência Prático e Didático das Funções da DriverLib para Microcontroladores Texas Instruments C2000™**

[🇧🇷 Visão Geral (Português)](#-sobre-o-projeto) • [📚 Módulos & Docs](#-módulos-e-documentação) • [⚡ Exemplo Rápido](#-exemplo-prático-com-driverlib) • [🗺️ Roadmap](#-roadmap-de-periféricos) • [🇺🇸 English Summary](#-english-summary)

---

</div>

## 📌 Sobre o Projeto

O desenvolvimento de firmware para microcontroladores de controle em tempo real da linha **Texas Instruments C2000™** (como a série **DSP28004x / TMS320F28004x**) tradicionalmente exigia manipular centenas de bits e registradores de baixo nível (`HWREG`), resultando em código verboso, de difícil manutenção e propenso a erros.

A **DriverLib** (inclusa no pacote oficial **C2000Ware**) introduz uma camada robusta de abstração de periféricos via APIs em C, tornando a configuração de periféricos complexos muito mais legível, reutilizável e padronizada.

No entanto, navegar pelos densos manuais técnicos (*Technical Reference Manuals - TRM*) da Texas Instruments pode ser demorado. Este repositório tem como missão fornecer um **guia de consulta rápido, claro e com exemplos práticos** para cada função, estrutura e registrador da DriverLib, detalhando:
- **Propósito** de cada função;
- **Parâmetros**, tipos de dados e valores válidos;
- **Registradores internos afetados**;
- **Exemplos práticos de código em C** prontos para uso;
- **Arquitetura de submódulos** explicada de forma conceitual e prática.

---

## 🎯 Dispositivos e Famílias Suportadas

O conteúdo deste repositório é baseado principalmente no microcontrolador **TMS320F28004x (F280049C)**, sendo diretamente aplicável ou facilmente portável para as demais famílias C2000™ Tipo 4 e superiores:

| Família / Dispositivo | Gerações Principais | Status na DriverLib |
|:---|:---|:---:|
| **F28004x** (ex: F280049C) | Piccolo™ Real-Time Control | ✅ Base Principal |
| **F28002x / F28003x** | Geração Compacta de Controle | ✅ Compatível |
| **F280013x / F280015x** | Linha Econômica de Entrada | ✅ Compatível |
| **F2837x / F2838x** | Delfino™ / Dual-Core & Conectividade | ✅ Compatível |
| **F28P55x / F28P65x** | Nova Geração C2000™ | ✅ Compatível |

---

## 📚 Módulos e Documentação

A documentação é dividida por periférico. Cada módulo conta com descrições detalhadas de suas funções e submódulos internos:

| Módulo | Descrição do Periférico | Guia em Português | English Guide | Status |
|:---|:---|:---:|:---:|:---:|
| **EPWM** | *Enhanced Pulse Width Modulation* — Geração de PWM de alta precisão, controle de inversores, conversores e motores | [📖 Guia Completo](EPWM/EPMW_portugues.md) | [📖 English Doc](EPWM/EPWM.md) | Completo |
| **ADC** | *Analog-to-Digital Converter* — Amostragem de sinais analógicos, SOC (Start of Conversion) e triggers | *Em breve* | *Planned* | Planejado |
| **GPIO** | *General Purpose Input/Output* — Configuração de pinos, modos de multiplexação e qualificação de entrada | *Em breve* | *Planned* | Planejado |
| **eCAP** | *Enhanced Capture* — Captura de tempo de bordas de sinal e medição de período/frequência | *Em breve* | *Planned* | Planejado |
| **eQEP** | *Enhanced Quadrature Encoder Pulse* — Interface com encoders ópticos e sensores de posição/velocidade | *Em breve* | *Planned* | Planejado |
| **CMPSS** | *Comparator Subsystem* — Comparadores analógicos rápidos com DAC interno e filtragem digital | *Em breve* | *Planned* | Planejado |
| **SCI / UART** | *Serial Communications Interface* — Comunicação serial assíncrona (UART) | *Em breve* | *Planned* | Planejado |
| **SPI / I2C** | Interfaces de comunicação síncrona para sensores e memórias | *Em breve* | *Planned* | Planejado |
| **CAN / DCAN** | *Controller Area Network* — Rede de comunicação automotiva e industrial | *Em breve* | *Planned* | Planejado |
| **CLA** | *Control Law Accelerator* — Coprocessador matemático independente de 32 bits | *Em breve* | *Planned* | Planejado |

### 🔍 Destaques do Módulo EPWM

O capítulo do [EPWM (Português)](EPWM/EPMW_portugues.md) cobre extensivamente mais de 1.600 linhas com explicações didáticas para todos os submódulos da arquitetura:
- **Time-Base (TB):** Prescalers (`TBCLK`, `HSPCLKDIV`), contagem up/down e sincronização de fase (`TBPHS`).
- **Counter-Compare (CC):** Modos de carga Shadow e registradores `CMPA`, `CMPB`, `CMPC`, `CMPD`.
- **Action-Qualifier (AQ):** Definições de ações nos pinos `EPWMxA` e `EPWMxB` (Set, Clear, Toggle).
- **Dead-Band (DB):** Gerador de banda morta complementar para evitar curto-circuito de braço (*shoot-through*).
- **Chopper (PC):** Modulação em alta frequência para acionamento por transformadores de pulso.
- **Trip-Zone (TZ) & Digital-Compare (DC):** Proteção imediata de hardware por sobrecorrente / sobretensão.
- **Event-Trigger (ET):** Disparo síncrono de interrupções e conversões ADC via SOCA / SOCB.
- **Global Load & Lock Registers:** Atualização síncrona de múltiplos registradores e bloqueio de segurança contra escrita.
- **High Resolution PWM (HRPWM):** Posicionador de microborda (MEP) com precisão de ~150 picosegundos.

---

## ⚡ Exemplo Prático com DriverLib

Abaixo está um exemplo demonstrativo de configuração simplificada de um sinal PWM de 20 kHz simétrico (Up-Down count) com duty cycle de 50% utilizando a função de alto nível `EPWM_configureSignal()` da DriverLib:

```c
#include "driverlib.h"
#include "device.h"

void initEPWM1(void)
{
    EPWM_SignalParams pwmParams;

    // 1. Configura o comportamento do EPWM em modo de depuração (pausa pelo debugger)
    EPWM_setEmulationMode(EPWM1_BASE, EPWM_EMULATION_FREE_RUN);

    // 2. Preenche os parâmetros operacionais da forma de onda desejada
    pwmParams.freqInHz      = 20000.0f;                       // Frequência: 20 kHz
    pwmParams.dutyValA      = 0.50f;                          // Duty cycle no canal A: 50%
    pwmParams.dutyValB      = 0.50f;                          // Duty cycle no canal B: 50%
    pwmParams.invertSignalB = true;                           // Canal B complementar invertido
    pwmParams.sysClkInHz    = 100000000.0f;                   // Frequência do SYSCLK: 100 MHz (DSP28004x)
    pwmParams.tbCtrMode     = EPWM_COUNTER_MODE_UP_DOWN;      // Modo de contagem Up-Down (simétrico)
    pwmParams.tbClkDiv      = EPWM_CLOCK_DIVIDER_1;           // Prescaler TBCLK: 1
    pwmParams.tbHSClkDiv    = EPWM_HSCLOCK_DIVIDER_1;         // Prescaler HSPCLK: 1

    // 3. Aplica todos os cálculos de registradores (TBPRD, CMPA, CMPB, AQ) automaticamente
    EPWM_configureSignal(EPWM1_BASE, &pwmParams);
}
```

---

## 📂 Estrutura do Repositório

```text
driverlib-reference/
├── README.md                 # Página inicial e guia geral de navegação
└── EPWM/                     # Módulo Enhanced Pulse Width Modulation
    ├── EPMW_portugues.md     # Documentação detalhada em Português (~1.600 linhas)
    └── EPWM.md               # Documentação de referência em Inglês
```

---

## 🛠️ Requisitos de Software e Ambiente

Para utilizar as funções descritas neste repositório em seus projetos:

1. **IDE:** [Code Composer Studio (CCS)](https://www.ti.com/tool/CCSTUDIO) v12.0 ou superior.
2. **SDK:** [Texas Instruments C2000Ware](https://www.ti.com/tool/C2000WARE) (v4.x ou mais recente recomendada).
3. **Compilador:** TI C28x Compiler (incluso no CCS).
4. **Header principal:** Inclua `#include "driverlib.h"` no início do seu código-fonte para ter acesso a todas as declarações de funções e tipos enumerados.

---

## 🗺️ Roadmap de Periféricos

- [x] **EPWM** (Driver base, submódulos avançados, exemplos e HRPWM)
- [ ] **ADC** (Configuração de canais, amostragem, calibração e triggers síncronos)
- [ ] **GPIO** (Configuração de MUX, pull-up, direção e qualificação por amostragem)
- [ ] **eCAP / eQEP** (Medição de período e decodificação de quadratura para encoders)
- [ ] **SCI / UART** (Transmissão, recepção com FIFO e interrupções)
- [ ] **SPI & I2C** (Comunicação com periféricos externos e sensores)
- [ ] **CAN / DCAN** (Mailboxes, filtros e comunicação automotiva)
- [ ] **CLA** (Compartilhamento de memória e tarefas em tempo real)

---

## 🤝 Como Contribuir

Contribuições são muito bem-vindas! Se você deseja colaborar adicionando a documentação de um novo módulo, corrigindo informações ou adicionando exemplos de código:

1. Faça um **Fork** deste repositório.
2. Crie uma branch para sua funcionalidade ou correção:
   ```bash
   git checkout -b feature/novo-modulo-adc
   ```
3. Mantenha a estrutura padronizada para as funções:
   - **Propósito**
   - **Sintaxe**
   - **Parâmetros**
   - **Valor de Retorno**
   - **Descrição**
   - **Exemplo de Código**
4. Faça commit das alterações:
   ```bash
   git commit -m "docs: adiciona guia de referencia da DriverLib para modulo ADC"
   ```
5. Envie para o seu fork (`git push origin feature/novo-modulo-adc`) e abra um **Pull Request**.

---

## 🌐 English Summary

Welcome to the **C2000™ DriverLib Reference Guide**!

This repository provides clear, accessible, and practical documentation for developers working with **Texas Instruments C2000™ Real-Time Microcontrollers** (DSP28004x / F280049C and related families) using the **C2000Ware DriverLib**.

### Key Highlights:
- **Comprehensive EPWM Chapter:** Detailed reference covering fundamental functions, auxiliary APIs, and advanced submodules (Time-Base, Counter-Compare, Action-Qualifier, Dead-Band, Trip-Zone, Chopper, Event-Trigger, Global Load, and High Resolution PWM).
- **Bilingual Documentation:** Available in [English](EPWM/EPWM.md) and [Portuguese](EPWM/EPMW_portugues.md).
- **Ready-to-use C Examples:** Practical snippets tested for C2000Ware.
- **Future Expansions:** Detailed roadmap covering ADC, GPIO, eCAP, eQEP, SCI, SPI, CAN, and CLA modules.

Feel free to browse the chapters, fork the repository, and submit pull requests or issues!

---

## 📖 Recursos e Referências Oficiais da Texas Instruments

- [Guia Oficial de Controle em Tempo Real da TI (SLYY211)](https://www.ti.com/lit/eb/slyy211/slyy211.pdf)
- [C2000 ePWM Developer’s Guide (SPRAD12)](https://www.ti.com/lit/sprad12)
- [Treinamento Oficial ePWM para MCUs C2000](https://www.ti.com/video/series/C2000-enhanced-pulse-width-modulator.html)
- [C28x Academy - Módulo EPWM](https://dev.ti.com/tirex/explore/node?node=A__AaKBh5Iw4k3VWS3akgXWzA__C28X-ACADEMY__1sbHxUB__LATEST)
- [Fórum Técnico TI E2E™](https://e2e.ti.com/support/microcontrollers/c2000/)

---

<div align="center">

Desenvolvido para a comunidade de engenharia de sistemas embarcados e controle digital em tempo real.

⭐ Se este guia foi útil para seus estudos ou projetos com C2000™, considere deixar uma estrela no repositório!

</div>
