# 🌊 Simulação de Escoamento - Sistema de Tubulações

Aplicação web interativa para análise completa de sistemas de escoamento em tubulações e canais abertos, desenvolvida com Streamlit.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-1.31.0-red)

## 📋 Descrição

Esta aplicação permite realizar simulações avançadas de escoamento de fluidos em sistemas de tubulações em série, incluindo:
- Análise de múltiplos trechos com diferentes diâmetros e materiais
- Cálculo de perdas de carga distribuídas e localizadas
- Perfil de pressão ao longo do sistema
- Análise de canais abertos
- Simulações paramétricas e comparações

## ✨ Funcionalidades

### 🔧 Configuração de Fluidos
- **Fluidos pré-configurados**: Água, Ar, Óleo leve, Gás ideal
- **Fluido personalizado**: Defina densidade e viscosidade
- **Temperatura variável**: -50°C a 500°C
- **Cálculo automático** de propriedades termofísicas

### 📊 Sistema de Tubulações
- ✅ Múltiplos trechos em série
- ✅ 6 materiais diferentes (PVC, Cobre, Aço comercial, Aço galvanizado, Concreto, Ferro fundido)
- ✅ Diâmetros e comprimentos variáveis
- ✅ Desníveis de elevação
- ✅ Acessórios completos:
  - Contrações e expansões
  - Curvas de 90°
  - Válvulas (gaveta, globo, esfera, retenção)
  - Tês (passagem direta e lateral)

### 🌊 Canais Abertos
- Cálculo de profundidade normal e crítica
- Número de Froude e classificação de regime
- Equação de Manning
- Geometria hidráulica completa

### 📈 Simulações Avançadas
- Variação de vazão com gráficos de perda de carga e velocidade
- Variação de pressão de entrada
- Comparação entre diferentes materiais
- Gráficos interativos exportáveis

### ⚠️ Verificações Automáticas
- Alertas de velocidade fora das faixas recomendadas
- Validação de regime de escoamento (laminar, transição, turbulento)
- Classificação de regime em canais (subcrítico, crítico, supercrítico)

## 🚀 Instalação

### Pré-requisitos
- Python 3.8 ou superior
- pip (gerenciador de pacotes Python)

### Passo a passo

1. **Clone ou baixe o repositório:**
```bash
git clone https://github.com/seu-usuario/escoamento-app.git
cd escoamento-app
```

2. **Crie um ambiente virtual (recomendado):**
```bash
python -m venv venv
```

3. **Ative o ambiente virtual:**
```bash
# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate
```

4. **Instale as dependências:**
```bash
pip install -r requirements.txt
```

5. **Execute a aplicação:**
```bash
streamlit run app.py
```

6. **Acesse no navegador:**
```
http://localhost:8501
```

## 📁 Estrutura do Projeto

```
project/
│
├── app.py                      # Arquivo principal da aplicação
├── requirements.txt            # Dependências do projeto
├── README.md                   # Documentação
│
├── config/                     # Configurações
│   ├── __init__.py
│   └── settings.py            # Constantes e configurações gerais
│
├── utils/                      # Utilitários e cálculos
│   ├── __init__.py
│   ├── fluid_properties.py    # Propriedades dos fluidos
│   ├── loss_coefficients.py   # Coeficientes de perda K
│   └── calculations.py        # Cálculos de escoamento
│
├── components/                 # Componentes da interface
│   ├── __init__.py
│   ├── styles.py              # CSS customizado
│   ├── sidebar.py             # Sidebar de configuração
│   └── pipe_config.py         # Interface de tubos
│
└── tabs/                       # Abas da aplicação
    ├── __init__.py
    ├── pipe_system.py         # Sistema de tubulações
    ├── open_channels.py       # Canais abertos
    ├── simulations.py         # Simulações
    └── about.py               # Informações
```

## 📊 Métodos de Cálculo

### Escoamento em Tubos

**Número de Reynolds:**
```
Re = (ρ × V × D) / μ
```

**Fator de Atrito (Colebrook-White):**
```
1/√f = -2 × log₁₀[(ε/D)/3.7 + 2.51/(Re×√f)]
```

**Perda de Carga Distribuída (Darcy-Weisbach):**
```
hf = f × (L/D) × (V²/2g)
```

**Perdas Localizadas:**
```
hL = K × (V²/2g)
```

### Canais Abertos

**Equação de Manning:**
```
Q = (1/n) × A × R^(2/3) × S^(1/2)
```

**Número de Froude:**
```
Fr = V / √(g × y)
```

## 🎯 Exemplos de Uso

### Exemplo 1: Sistema de Água Simples
1. Selecione "Água" como fluido
2. Configure temperatura (20°C)
3. Defina pressão inicial (300 kPa)
4. Entre com vazão ou velocidade
5. Configure um ou mais trechos de tubulação
6. Visualize resultados e perfil de pressão

### Exemplo 2: Comparação de Materiais
1. Configure o sistema base
2. Vá para aba "Simulações"
3. Compare perdas de carga entre diferentes materiais
4. Escolha o material mais adequado

### Exemplo 3: Canal Aberto
1. Vá para aba "Canais Abertos"
2. Entre com vazão e largura do canal
3. Defina inclinação e coeficiente de Manning
4. Analise profundidades normal e crítica

## 🛠️ Tecnologias Utilizadas

- **[Streamlit](https://streamlit.io/)** - Framework web para Python
- **[Fluids](https://github.com/CalebBell/fluids)** - Biblioteca de engenharia de fluidos
- **[Plotly](https://plotly.com/python/)** - Gráficos interativos
- **[Pandas](https://pandas.pydata.org/)** - Manipulação de dados
- **[NumPy](https://numpy.org/)** - Computação numérica

## 📖 Documentação Adicional

### Coeficientes K (Perdas Localizadas)

| Acessório | K |
|-----------|---|
| Contração | 0.5 × (1 - β²) |
| Expansão | (1 - β²)² |
| Curva 90° | 0.3 |
| Válvula gaveta | 0.15 |
| Válvula globo | 10.0 |
| Válvula esfera | 0.05 |
| Válvula retenção | 2.5 |
| Tê passagem | 0.6 |
| Tê lateral | 1.8 |

### Velocidades Recomendadas

**Água:**
- Mínima: 0,5 m/s (evita sedimentação)
- Máxima: 3,0 m/s (evita erosão e ruído)
- Sucção: 0,6 a 1,5 m/s
- Recalque: 1,5 a 2,5 m/s

**Ar:**
- Máxima: 15 m/s

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:
- Reportar bugs
- Sugerir novas funcionalidades
- Enviar pull requests
- Melhorar a documentação

## 👨‍💻 Autor

Desenvolvido para fins educacionais e profissionais em Engenharia de Fluidos.

## 📞 Suporte

Para dúvidas ou sugestões:
- Abra uma issue no GitHub
- Entre em contato através do e-mail

## 🎓 Referências

- Fox, R.W., McDonald, A.T., Pritchard, P.J. - "Introdução à Mecânica dos Fluidos"
- White, F.M. - "Fluid Mechanics"
- Munson, B.R., Young, D.F., Okiishi, T.H. - "Fundamentals of Fluid Mechanics"

---

⭐ Se este projeto foi útil para você, considere dar uma estrela no GitHub!
