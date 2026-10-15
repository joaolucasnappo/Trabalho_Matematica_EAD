# Do sinal ao espectro: um analisador e filtro de sinais de ECG

Sistematização da disciplina de Métodos Matemáticos: Séries de Fourier → Transformada de Fourier → Transformada de Laplace.

## Integrantes

- Enzo Gutiérrez Pereira
- Felipe Abrantes
- Juliano Araújo
- João Lucas Nappo
- Eduardo Regueiro

## Vídeo de apresentação

Link: [_a inserir_](https://youtu.be/TR0KhKRmxJw)

## O que foi feito

Trabalhamos com dois trechos de eletrocardiograma do [MIT-BIH Arrhythmia Database](https://physionet.org/content/mitdb/1.0.0/) (PhysioNet), amostrados a 360 Hz, e comparamos dois tipos de filtro em cada um.

| | Sinal A | Sinal B |
|---|---|---|
| Registro | 111, de 30 s a 40 s | 203, de 10 s a 20 s |
| Problema | interferência de 60 Hz da rede elétrica | deriva da linha de base |
| Filtro analógico | rejeita-faixa (*notch*) de 2ª ordem, Q = 30 | passa-altas RC de 1ª ordem, 0,5 Hz |
| Filtro de comparação | máscara ideal no espectro | máscara ideal no espectro |

| Etapa | Conteúdo |
|---|---|
| 1 | Série de Fourier da onda quadrada: coeficientes, forma complexa, convergência e fenômeno de Gibbs |
| 2 | FFT dos dois sinais, amostragem e Nyquist, interpretação do espectro |
| 3 | Filtragem no domínio da frequência e reconstrução pela transformada inversa |
| 4 | Função de transferência H(s) por Laplace, mapa de polos e zeros, estabilidade e ligação com o espectro |

O relatório está no próprio notebook, nas células de texto que acompanham cada gráfico.

## Arquivos

```
sistematizacao.ipynb   notebook com o código e o relatório das quatro etapas
data/                  trechos de ECG usados (.csv: tempo em s, amplitude em mV)
pyproject.toml         dependências do projeto
uv.lock                versões exatas das dependências
```

## Como executar

**No Google Colab:** abra
<https://colab.research.google.com/github/joaolucasnappo/Trabalho_Matematica_EAD/blob/master/sistematizacao.ipynb>
e use *Ambiente de execução → Executar tudo*. Os dados são baixados do PhysioNet automaticamente.

**Localmente, com [uv](https://docs.astral.sh/uv/):**

```bash
uv sync
uv run jupyter lab sistematizacao.ipynb
```

Para reexecutar tudo pela linha de comando:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace sistematizacao.ipynb
```

Se a pasta `data/` for apagada, o notebook baixa novamente os trechos do PhysioNet.

## Dados

Moody, G. B.; Mark, R. G. *The impact of the MIT-BIH Arrhythmia Database*. IEEE Eng. in Med. and Biol. 20(3):45-50, 2001. Disponível no PhysioNet sob a licença Open Data Commons Attribution v1.0.
