# estudo-ciberseguranca-dio
Projeto para conclusão do curso de Cibersegurança do Santander Open Academy em parceria com a DIO, 2025.

**Atenção:** Esse projeto tem finalidade estritamente educacional. Os resultados demonstrados foram obtidos em testes realizados em um ambiente virtual isolado. É recomendado que não se aplique as técnicas aqui descritas em sistemas reais - o objetivo é apenas informar a respeito de vulnerabilidades e meios de defesa. 

# Fundamentos de Cibersegurança: Projeto Teórico

Este repositório documenta o aprendizado prático e teórico adquirido durante o curso de Cibersegurança do Santander Open Academy em parceria com a DIO. O projeto consiste no planejamento completo de um Pentest, simulando a atuação de um *Red Team* em um cenário corporativo, desde a coleta de informações até a análise de vulnerabilidades.

## Resumo do Projeto
O objetivo deste estudo foi estruturar o ciclo de vida de um ataque ético, demonstrando domínio sobre as ferramentas e metodologias utilizadas por profissionais de segurança ofensiva.
* **Metodologia:** PTES (Penetration Testing Execution Standard).
* **Tipo de Teste:** Black Box (Simulação de um atacante externo sem informações prévias).
* **Foco:** Infraestrutura de Redes, Aplicações Web e Fator Humano (Engenharia Social).

##  Cenário Hipotético de Ataque (Estudo de Caso)
Para consolidar o conhecimento, foi desenvolvido o seguinte cenário de ataque contra uma empresa fictícia ("ABC Corp"), aplicando as técnicas estudadas:

### 1. Reconhecimento e OSINT (A Coleta)
O primeiro passo seria mapear a superfície de ataque sem interagir diretamente com o alvo.
* **Ação:** Utilização de **Google Dorks** (`site:abccorp.com filetype:pdf`) para encontrar documentos públicos esquecidos.
* **Análise:** Uso da ferramenta **FOCA** nesses arquivos para extrair metadados, identificando nomes de usuários internos, versões de software (ex: "Microsoft Word 2013") e sistemas operacionais.
* **Infraestrutura:** Consulta ao **Shodan** para identificar servidores da empresa expostos à internet e verificar se há serviços vulneráveis (ex: Câmeras, RDP ou bancos de dados sem senha).

### 2. Varredura e Enumeração
Com os IPs identificados no passo anterior, o foco passaria para a varredura ativa.
* **Ferramenta:** **Nmap**.
* **Comando Teórico:** `nmap -sV -sC -O abccorp.com` (Para detectar versões de serviços, rodar scripts padrão e identificar o SO).
* **Objetivo:** Descobrir portas abertas (ex: Porta 21 FTP, Porta 80 HTTP) e versões desatualizadas de serviços que possuam CVEs (vulnerabilidades conhecidas) associadas.

### 3. Exploração de Vulnerabilidades
* **Vetor Técnico:** Caso o Nmap identificasse um serviço FTP desatualizado, a estratégia seria buscar um *exploit* público para aquela versão específica.
* **Vetor Humano (Engenharia Social):** Paralelamente, com os e-mails descobertos na fase de OSINT, seria elaborada uma campanha de **Phishing** simulada. O e-mail conteria um "aviso de segurança urgente", levando o usuário a uma página falsa (clonada com ferramentas como *Social Engineering Toolkit*) para captura de credenciais.

### 4. Anonimato e Segurança
Durante toda a operação teórica, a navegação seria realizada através do **Tor Browser** ou roteada via **VPN/Proxy** para ocultar o endereço IP de origem, garantindo a segurança operacional (OpSec).

## Ferramentas e Tecnologias Estudadas
Abaixo estão as principais tecnologias analisadas no projeto:

* **Sistemas Operacionais:** Kali Linux (Offensive), Tails (Privacidade) e Windows.
* **Reconhecimento:** Google Hacking, Shodan, Maltego.
* **Varredura:** Nmap, Scripts NSE.
* **Análise:** FOCA (Metadados).
* **Redes:** Protocolos TCP/IP, Conceitos de Portas e Endereçamento IP.

## Conclusão e Mitigação
Este estudo de caso evidencia que a segurança deve ser tratada em camadas. Para o cenário hipotético acima, as recomendações de defesa (Blue Team) seriam:
1.  **Atualização de Patches:** Manter serviços (como o FTP detectado) sempre atualizados.
2.  **Limpeza de Metadados:** Remover informações sensíveis de documentos públicos.
3.  **Treinamento:** Conscientizar colaboradores para identificar tentativas de Phishing.
