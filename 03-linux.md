# 03 — Linux

📚 **Cursos:** Formação Linux — Alura · OverTheWire: Bandit  
🔗 **Fontes:** alura.com.br · overthewire.org/wargames/bandit  
✅ **Status:** Concluído  
📅 **Período:** Julho/2026

---

## O que é Linux e por que importa para dev

Linux é o sistema operacional dominante em servidores, cloud e ambientes de produção. Como dev backend, você vai deployar, debugar e operar em Linux — entender o terminal não é opcional.

---

## Navegação e manipulação de arquivos

```bash
pwd          # mostra o diretório atual
ls           # lista arquivos e pastas
ls -la       # lista com permissões e arquivos ocultos
cd pasta/    # entra no diretório
cd ..        # volta um nível
mkdir nome   # cria diretório
cp orig dest # copia arquivo
mv orig dest # move ou renomeia arquivo
cat arquivo  # exibe conteúdo do arquivo
```

---

## Permissões

```bash
chmod 755 arquivo    # rwx para dono, rx para grupo e outros
chmod +x script.sh   # adiciona permissão de execução
sudo comando         # executa como superusuário
su                   # troca para usuário root
```

### Como ler permissões (`ls -la`)

```
-rwxr-xr-- 1 octavio devs 1234 Jan 01 arquivo.sh
 ↑↑↑ ↑↑↑ ↑↑↑
 │   │   └── outros (r--)
 │   └─────── grupo  (r-x)
 └─────────── dono   (rwx)
```

| Letra | Significado |
|---|---|
| `r` | leitura (read) |
| `w` | escrita (write) |
| `x` | execução (execute) |
| `-` | sem permissão |

---

## Redirecionamento e Pipes

```bash
# Redirecionamento de saída
comando > arquivo.txt    # sobrescreve
comando >> arquivo.txt   # acrescenta

# Redirecionamento de entrada
comando < arquivo.txt

# Pipe — encadeia comandos
ls -la | grep ".md"      # filtra saída do ls
cat log.txt | sort | uniq
```

> O pipe `|` é um dos conceitos mais poderosos do Linux — a saída de um comando vira a entrada do próximo.

---

## Busca e filtragem de texto

```bash
grep "padrão" arquivo        # busca linha com padrão
grep -r "padrão" pasta/      # busca recursiva
grep -E "regex" arquivo      # regex estendido

# awk — processa colunas de texto
awk '{print $1}' arquivo     # imprime primeira coluna
awk -F: '{print $1}' /etc/passwd   # define separador

# strings — extrai texto legível de binários
strings binário | grep algo

# file — identifica tipo do arquivo
file arquivo.zip
```

---

## Compactação e arquivamento

```bash
# tar
tar -czf nome.tar.gz pasta/   # compacta com gzip
tar -xzf nome.tar.gz           # descompacta
tar -cjf nome.tar.bz2 pasta/  # compacta com bzip2

# gzip
gzip arquivo       # compacta → gera arquivo.gz
gunzip arquivo.gz  # descompacta

# bzip2
bzip2 arquivo      # compacta → gera arquivo.bz2
bunzip2 arquivo.bz2
```

---

## Editores de texto no terminal

```bash
# Vim
vim arquivo.txt
# Modos: Normal (navegar) → Insert (i para editar) → Command (:w salva, :q sai, :wq salva e sai)

# Nano — mais simples
nano arquivo.txt
# Ctrl+O salva · Ctrl+X sai · Ctrl+W busca
```

---

## Shell Script

```bash
#!/bin/bash          # shebang — define o interpretador

# Variáveis
NOME="Octavio"
echo "Olá, $NOME"

# Condicional
if [ "$NOME" == "Octavio" ]; then
  echo "Correto"
fi

# Loop
for i in 1 2 3; do
  echo "Item $i"
done

# Execução
chmod +x script.sh
./script.sh
```

---

## Comandos úteis variados

```bash
echo "texto"          # imprime texto no terminal
curl URL              # faz requisição HTTP
curl -X POST URL      # requisição POST
ssh user@host         # conecta a servidor remoto
ssh -i chave.pem user@host   # com chave privada
```

---

## Agendamento e serviços

```bash
# crontab — agendamento de tarefas
crontab -e            # edita as tarefas agendadas
# formato: minuto hora dia mês dia_semana comando
# 0 * * * * /script.sh → roda todo início de hora

# systemd — gerenciador de serviços
systemctl start nginx
systemctl stop nginx
systemctl status nginx
systemctl enable nginx   # inicia com o sistema
```

---

## SSH e AWS básico

```bash
# Conectar em instância EC2
ssh -i chave.pem ubuntu@ip-da-instancia

# Copiar arquivo para servidor
scp arquivo.txt user@host:/destino/
```

AWS básico visto nesta fase: EC2 (instâncias), acesso via SSH, noção de regiões e IPs públicos. Profundidade vai entrar na Fase 2 com Cloud Practitioner.

---

## Conceito central

> No Linux, você não memoriza comandos — você entende o que quer fazer e busca como fazer.  
> O terminal é uma ferramenta de precisão: pipes, redirecionamento e grep encadeados fazem em segundos o que uma UI levaria minutos.

---

## O que ainda consolida só com uso diário

- Intuição para construir pipes complexos
- Regex avançado no grep e awk
- Scripting com condicionais e loops reais
- Debugging de permissões e processos em produção
