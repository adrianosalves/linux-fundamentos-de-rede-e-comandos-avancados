# Linux Fundamentos de Rede e Comandos Avancados

net-tools: Pacotes de Ferramentas para rede.

sudo apt install net-tools

# comando ifconfig

É um comando que gerencia as interfaces de rede no Linux.

abaixo temos um placa de rede wifi:

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.103  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a4f9:dd2:62f4:1f90  prefixlen 64  scopeid 0x20<link>
        ether 94:53:30:4d:e8:35  txqueuelen 1000  (Ethernet)
        RX packets 5039  bytes 3422600 (3.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5914  bytes 1476015 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0       

Exemplo:

 inet 192.168.0.103 - Rede Local
 netmask 255.255.255.0  - Rede local diferente da Rede publica
 broadcast 192.168.0.255 - Rede de Broadcast 
  inet6 fe80::a4f9:dd2:62f4:1f90 - IPv6 usa numero hexdecimal  
  ether 94:53:30:4d:e8:35 - Endereço fisico unico
  
abaixo temos o endere de loopback que representa a propria maquina:

  lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Loopback Local)
        RX packets 3677  bytes 397624 (397.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3677  bytes 397624 (397.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

# Comandos hostname, who, whoami e ping
  
hostname - Representa o nome do comando na rede.
whoaim  - Mostra nome do usuario logado na maquina
who - Mostra o nome do usuario logado na maquina e detalhes como data e hora.
ping - faz parte do protocolo ICMP enviando mensagens para o outro host está ativo ou não...
  
Exemplo:
  
$ping google.com
PING google.com (142.251.128.78) 56(84) bytes of data.
64 bytes from gru06s69-in-f14.1e100.net (142.251.128.78): icmp_seq=1 ttl=115 time=61.8 ms
64 bytes from gru06s69-in-f14.1e100.net (142.251.128.78): icmp_seq=2 ttl=115 time=60.1 ms
64 bytes from gru06s69-in-f14.1e100.net (142.251.128.78): icmp_seq=3 ttl=115 time=60.4 ms

# Commando dig
 
dig - Exibe informações sobre DNS
  
Exemplo 1:  Exibe todas as infomações sobre DNS do google
  
$ dig google.com

; <<>> DiG 9.16.6-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55491
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		217	IN	A	142.251.128.78

;; Query time: 8 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: qua abr 27 12:05:19 -03 2022
;; MSG SIZE  rcvd: 55
  
Exemplo 2:  Exibe apenas o IP do google.com
  
$dig google.com +short
142.251.128.78


# Comandos traceroute e finger
  
traceroute - Exibe a rota que seu pacote de rede faz até o destino mostrando os nós(saltos). ate chegar o destino.
finger -   
  
Exemplo:
  
$ traceroute google.com
traceroute to google.com (142.251.128.78), 30 hops max, 60 byte packets
 1  _gateway (192.168.0.1)  6.979 ms  6.881 ms  6.785 ms
 2  131.72.164.251.prismatelcom.com.br (131.72.164.251)  6.692 ms  6.563 ms  6.439 ms
 3  * 198.18.0.121 (198.18.0.121)  4.308 ms  4.234 ms
 4  * * *
 5  10.5.9.182 (10.5.9.182)  33.191 ms  33.147 ms  33.041 ms
 6  * * *
 7  10.5.11.41 (10.5.11.41)  18.434 ms  18.329 ms  18.246 ms
 8  * * *
 9  * * *
10  10.5.20.66 (10.5.20.66)  66.593 ms  66.514 ms  66.400 ms
11  74.125.32.22 (74.125.32.22)  66.254 ms  62.235 ms  62.913 ms
12  * * *
13  142.251.53.178 (142.251.53.178)  60.934 ms 142.251.78.18 (142.251.78.18)  63.716 ms 142.251.53.176 (142.251.53.176)  66.967 ms
14  74.125.243.12 (74.125.243.12)  62.927 ms 142.251.76.129 (142.251.76.129)  61.244 ms 74.125.243.76 (74.125.243.76)  62.673 ms
15  172.253.67.188 (172.253.67.188)  62.581 ms gru06s69-in-f14.1e100.net (142.251.128.78)  62.381 ms 172.253.67.188 (172.253.67.188)  69.696 ms

 # Comando Whois
  
  whois - Exibe informações sobre um determinado dominio com muitos detalhes.
  
Exemplo:

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
Domain Name: google.com
Registry Domain ID: 2138514_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.markmonitor.com
Registrar URL: http://www.markmonitor.com
Updated Date: 2019-09-09T15:39:04+0000
Creation Date: 1997-09-15T07:00:00+0000
Registrar Registration Expiration Date: 2028-09-13T07:00:00+0000
Registrar: MarkMonitor, Inc.
Registrar IANA ID: 292
Registrar Abuse Contact Email: abusecomplaints@markmonitor.com
Registrar Abuse Contact Phone: +1.2083895770
Domain Status: clientUpdateProhibited (https://www.icann.org/epp#clientUpdateProhibited)
Domain Status: clientTransferProhibited (https://www.icann.org/epp#clientTransferProhibited)
Domain Status: clientDeleteProhibited (https://www.icann.org/epp#clientDeleteProhibited)
Domain Status: serverUpdateProhibited (https://www.icann.org/epp#serverUpdateProhibited)
Domain Status: serverTransferProhibited (https://www.icann.org/epp#serverTransferProhibited)
Domain Status: serverDeleteProhibited (https://www.icann.org/epp#serverDeleteProhibited)
Registrant Organization: Google LLC
Registrant State/Province: CA
Registrant Country: US
Registrant Email: Select Request Email Form at https://domains.markmonitor.com/whois/google.com
Admin Organization: Google LLC
Admin State/Province: CA
Admin Country: US
Admin Email: Select Request Email Form at https://domains.markmonitor.com/whois/google.com
Tech Organization: Google LLC
Tech State/Province: CA
Tech Country: US
Tech Email: Select Request Email Form at https://domains.markmonitor.com/whois/google.com
Name Server: ns3.google.com
Name Server: ns1.google.com
Name Server: ns2.google.com
Name Server: ns4.google.com
DNSSEC: unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2022-04-27T15:04:14+0000 <<<

# Comando Finger
                                                                
finger - Exibe informações do usuario logado na maquina inclusive telefone.
                                                                
$finger 
Login     Name       Tty      Idle  Login Time   Office     Office Phone
alvesnet  alvesnet   tty7     3:37  Apr 27 08:37 (:0)
                                                        
# Comandos
                                                                
ifconfig - Exibe informações sobre a interface de rede e IP
                                                                
hostname -  Exibe informações sobre o host.
                                                                
hostname -i -  Exibe o numero do endereço loopback do host
                                                                
hostname -I -  Exibe o endereço ip da rede
                                                                
dig host - Exibe informaçoes sobre o DNS de um host
                                                                
dig host +short - Exibe o numero IP de um host
                                                                
w - Exibe informações detalhadas sobre o usuario do computador na rede
                                                                
who - Exibe informações curtas sobre o usuario.
                                                                
whoami - Exibe informação da conta do usuarios.
                                                                
tracertroute - Exibe informações obre a rota da sua rede até o host de destino.
                                                                
ping - Teste um hosts se esta ativo
                                                                
finger - Exibe informações detalhadas sobre um determinado usuario.

# Linux comandos diversos
                                                                
history - Exibe o historico dos comandos digitados
                                                                
history -c - Paga todo o historico                                                                

nl - Exibi o conteudo do arquivo e exibe quantidade das linhas
                                                                
wc -l - Contas o numero de linhas incluido o espaço
                                                                
wc -w - Conta o numero de palavaras.
                                                                
alias hh=history - Cria um alias com nome hh para executar comando history
                                                                
alias trc=tracerout - Cria um alias com nome hh para executar comando tracertroute                                                               

ls -a - Exibe arquivos e pastas e arquivos ocultos.

ls -F - Exibe / em cada diretorio
                                                                
cmp - Exibe comparacao entre dois arquivo se exite algum vazio      
                                                                
diff - Exibe o comparacao entre dois arquivo e sinaliza..

sort -n - Exibe o conteudo da saida do arquivo em ordem numerica
                                                                
last reboot - Exibe a informação sobre a reinicialização do sistema                                                                
                                                                
route -n - Exibe todas as tabelas de roteamento do sistema.
                                                                
time tracertoute www.google.com - Exibe o calculo em tempo real da execução do processo.

uptime -  Exibe o tempo que o sistema está em execução.
                                                                
cowsay - Exibe uma vaquiha que fala. 

xcowsay - Exibie vaquinha em 3D

cmatrix - Exibe na console o efeito matrix na console.                                                                
                                                                
initi 0 - Desliga o computador imediatamente.

telinit 0 - Desliga o computador imediatamente.
                                                                
halt - Exibe autenticação para depois desligar!

seq - Imprime uma sequencia de numeros exemplo seq 1 10.

whereis - Exibe o caminho do programa e manual.

which - Exibe o caminho do arquivo.
                                                                
logout - Finaliza uma seção.

# Maquinas Virtual que pode ser acessado pelo Navegador.
                                                                
httos://bellard.org/jslinux     
                                                                
# Linux Gerenciamento de Pacotes
                                                                
Instalação, Atualização e Remoção de Pacotes

#. 1 Instalação:
                                                                
apt - É mais conhecido 

Exemplo de como instalar um pacote:                                                                
                                                                
sudo apt install nmap                                           

#.2 Atualização

sudo apt upgrade nmap
                                                                
#. 3 Remoção

sudo apt remove nmap
                                                                
# Atualização de Sistema

sudo apt update                                                                
                                                                
sudo apt upgrade
                         
ou
                                                                
sudo apt update && apt upgrade       

# Sites de Pacotes

pkgs.org
                                                                
rpm.pkgs.org
                     
# Instalação de pacotes dpkg:

dpkg -i 'nome do pacote.deb'

                                                                
                                                                
                                                                
                                                                

                                                                
                                                                                                                                
                                                                
                                                                

                                                                
                                                                
                                                                
                                                                
                                                                
                                                                
                                                                
                                                                
                                                                
                                                                
                                                              
  
  
  
  
  
  
 
 

