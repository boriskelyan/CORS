HTML
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Cours complet, stable et interactif sur les réseaux informatiques, TCP vs UDP, DHCP, DNS et NAT.">
    <title>Apprendre le Réseau - Version Corrigée avec Schémas</title>
    <style>
        :root {
            --bg-color: #f0f4f8;
            --card-bg: #ffffff;
            --text-color: #333333;
            --text-muted: #555555;
            --primary: #1a3c6e;
            --primary-hover: #14305a;
            --accent-blue: #e8eef5;
            --border-color: #e5eaf0;
            --box-bg: #f8fafc;
            --code-bg: #1e1e1e;
            --code-text: #f8f8f2;
        }

        [data-theme="dark"] {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-color: #f1f5f9;
            --text-muted: #94a3b8;
            --primary: #38bdf8;
            --primary-hover: #0284c7;
            --accent-blue: #334155;
            --border-color: #334155;
            --box-bg: #0f172a;
            --code-text: #38bdf8;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Arial, sans-serif; background: var(--bg-color); padding: 20px; color: var(--text-color); line-height: 1.65; }
        .container { max-width: 1040px; margin: auto; background: var(--card-bg); border-radius: 14px; padding: 28px; box-shadow: 0 6px 20px rgba(0,0,0,0.1); }
        
        .header { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; margin-bottom: 20px; }
        h1 { color: var(--primary); font-size: 1.9rem; }
        .subtitle { color: var(--text-muted); margin-bottom: 10px; }
        
        .theme-toggle { padding: 8px 14px; background: var(--accent-blue); color: var(--text-color); border: 1px solid var(--border-color); border-radius: 8px; cursor: pointer; font-weight: 600; }

        /* Navigation par onglets */
        .tabs { display: flex; gap: 10px; margin: 15px 0 18px; flex-wrap: wrap; border-bottom: 2px solid var(--border-color); padding-bottom: 12px; }
        .tab { padding: 11px 20px; background: var(--accent-blue); border: none; border-radius: 8px; cursor: pointer; font-weight: 600; color: var(--text-color); }
        .tab.active { background: var(--primary); color: white; }
        
        .content { display: none; padding: 8px 0; }
        .content.active { display: block; }
        
        /* Cartes & Blocs */
        .card { background: var(--box-bg); border-left: 5px solid var(--primary); padding: 18px 20px; margin: 16px 0; border-radius: 0 10px 10px 0; }
        .card h3 { color: var(--primary); margin-bottom: 10px; font-size: 1.25rem; }
        .card h4 { margin: 16px 0 7px; font-size: 1.08rem; color: var(--primary); }
        .card ul, .card ol { margin-left: 22px; margin-top: 6px; }
        .card li { margin-bottom: 5px; }
        
        .highlight { background: rgba(59, 130, 246, 0.1); padding: 12px 15px; border-radius: 8px; margin: 12px 0; border-left: 4px solid #3b82f6; }
        .schema-box { background: var(--card-bg); border: 1px solid var(--border-color); border-radius: 10px; padding: 15px; margin: 15px 0; text-align: center; overflow-x: auto; }
        
        pre { background: var(--code-bg); color: var(--code-text); padding: 14px; border-radius: 8px; overflow-x: auto; margin: 10px 0; font-size: 0.93rem; font-family: Consolas, Monaco, monospace; text-align: left; }
        code { font-family: Consolas, Monaco, monospace; }
        
        /* Terminal */
        .terminal { background: #0c0c0c; color: #00ff00; padding: 15px; border-radius: 8px; font-family: monospace; min-height: 180px; max-height: 300px; overflow-y: auto; margin: 10px 0; text-align: left; }
        .terminal-input-container { display: flex; gap: 8px; align-items: center; margin-top: 10px; }
        
        /* Boutons & Champs */
        .btn { padding: 10px 18px; background: #1a3c6e; color: white; border: none; border-radius: 7px; cursor: pointer; margin: 5px 3px 5px 0; font-weight: 500; }
        .btn:hover { opacity: 0.9; }
        .btn-secondary { background: #64748b; color: white; }
        input[type="text"] { padding: 9px 12px; border: 1px solid var(--border-color); background: var(--card-bg); color: var(--text-color); border-radius: 6px; width: 220px; max-width: 100%; font-size: 1rem; }
        
        /* Tableaux */
        table { width: 100%; border-collapse: collapse; margin: 12px 0; font-size: 0.94rem; }
        th, td { border: 1px solid var(--border-color); padding: 9px 11px; text-align: left; }
        th { background: #1a3c6e; color: white; }
        
        /* Quiz & Exercices */
        .quiz-question { margin: 16px 0; padding: 16px; background: var(--card-bg); border-radius: 10px; border: 1px solid var(--border-color); text-align: left; }
        .quiz-question p { font-weight: 600; margin-bottom: 8px; }
        .quiz-question label { display: block; margin: 6px 0; cursor: pointer; }
        .score-box { background: #1a3c6e; color: white; padding: 16px; border-radius: 10px; text-align: center; margin-top: 20px; font-size: 1.15rem; display: none; }
        .exo-box { background: rgba(249, 115, 22, 0.08); border-left: 5px solid #f97316; padding: 16px; margin: 14px 0; border-radius: 0 10px 10px 0; text-align: left; }

        @media print {
            body { background: white; color: black; }
            .tabs, .theme-toggle, .btn, input, .terminal-input-container { display: none !important; }
            .content { display: block !important; page-break-after: always; }
            .container { box-shadow: none; width: 100%; max-width: none; padding: 0; }
        }
        @media (max-width: 600px) { .container { padding: 16px; } h1 { font-size: 1.4rem; } }
    </style>
</head>
<body>
<div class="container">
    <div class="header">
        <div>
            <h1>📡 Le Guide du Réseau Informatique</h1>
            <p class="subtitle">Cours complet, TCP/IP, DHCP, DNS, NAT & Pratique</p>
        </div>
        <div>
            <button class="theme-toggle" onclick="toggleTheme()">🌙 Mode Sombre</button>
            <button class="btn btn-secondary" onclick="window.print()">🖨️ Imprimer / PDF</button>
        </div>
    </div>

    <div class="tabs">
        <button class="tab active" data-tab="cours">📘 Cours & Notions</button>
        <button class="tab" data-tab="services">⚙️ TCP, UDP, DHCP, DNS</button>
        <button class="tab" data-tab="cli">🖥️ Terminal CLI Interactif</button>
        <button class="tab" data-tab="outils">🧮 Outils & Calculateurs</button>
        <button class="tab" data-tab="exercices">✏️ Exercices</button>
        <button class="tab" data-tab="quiz">🧠 Quiz</button>
    </div>

    <div id="cours" class="content active">
        <div class="card">
            <h3>1. Qu'est-ce qu'un Protocole ?</h3>
            <p>Un <strong>protocole</strong> est un ensemble formel de règles et de conventions qui régit l’échange d’informations entre des unités connectées en réseau.</p>
            
            <h4>Protocoles orientés connexion vs non orientés connexion :</h4>
            <ul>
                <li><strong>Orienté connexion (ex: TCP) :</strong> Établit un dialogue formel (*handshake*) entre la source et le destinataire avant tout transfert. Les données sont préparées en <em>segments</em> (couche 4).</li>
                <li><strong>Non orienté connexion (ex: UDP) :</strong> Envoie directement les données sur le réseau sans circuit préalable.</li>
            </ul>

            <div class="highlight">
                <strong>Commutation de paquets vs Commutation de circuits :</strong><br>
                • <em>Commutation de paquets :</em> Circuit logique temporaire (ex: Internet / TCP/IP). Données découpées et acheminées indépendamment.<br>
                • <em>Commutation de circuits :</em> Circuit physique permanent et dédié (ex: téléphonie fixe).
            </div>
        </div>

        <div class="card">
            <h3>2. Origine Historique & Modèle TCP/IP</h3>
            <p>La forme actuelle de TCP/IP provient des recherches du <strong>DOD</strong> (<em>Department of Defense</em>) à travers le projet <strong>ARPANET</strong>, visant à concevoir un réseau décentralisé et résilient.</p>
            
            <div class="schema-box">
                <svg width="360" height="175" viewBox="0 0 360 175">
                    <rect x="30" y="5" width="300" height="32" rx="5" fill="#7c3aed"/><text x="180" y="25" fill="white" text-anchor="middle" font-size="13" font-weight="bold">4. Application (HTTP, DNS, FTP, SMTP)</text>
                    <rect x="30" y="45" width="300" height="32" rx="5" fill="#1d4ed8"/><text x="180" y="65" fill="white" text-anchor="middle" font-size="13" font-weight="bold">3. Transport (TCP, UDP)</text>
                    <rect x="30" y="85" width="300" height="32" rx="5" fill="#1e40af"/><text x="180" y="105" fill="white" text-anchor="middle" font-size="13" font-weight="bold">2. Internet / Réseau (IPv4, IPv6, ICMP)</text>
                    <rect x="30" y="125" width="300" height="32" rx="5" fill="#172554"/><text x="180" y="145" fill="white" text-anchor="middle" font-size="13" font-weight="bold">1. Accès Réseau (Ethernet, Wi-Fi)</text>
                </svg>
            </div>
        </div>
    </div>

    <div id="services" class="content">
        <div class="card">
            <h3>6. TCP vs UDP</h3>
            <p><strong>TCP</strong> est fiable, vérifie la réception et établit une connexion (*Three-Way Handshake*).</p>
            
            <pre>Client ─── [ SYN ] ────────► Serveur
Client ◄── [ SYN-ACK ] ────── Serveur
Client ─── [ ACK ] ────────► Serveur (Connexion établie)</pre>

            <div class="highlight">
                <strong>UDP</strong> est non orienté connexion : rapide, sans contrôle de livraison (parfait pour le streaming, la voix sur IP et le jeu vidéo).
            </div>
        </div>

        <div class="card">
            <h3>7. DHCP et DNS</h3>
            <h4>DHCP (Dynamic Host Configuration Protocol)</h4>
            <p>Attribue automatiquement la configuration IP selon la séquence <strong>DORA</strong> :</p>
            <pre>1. Discover  ► Le client cherche un serveur DHCP (Broadcast)
2. Offer     ► Le serveur propose une IP
3. Request   ► Le client confirme la demande d'IP
4. Acknowledge ► Le serveur valide le bail</pre>

            <h4 style="margin-top:15px;">DNS (Domain Name System)</h4>
            <p>Annuaire d'Internet traduisant les noms de domaine en adresses IP (ex: <code>google.com</code> ➔ <code>142.250.185.78</code>).</p>
        </div>

        <div class="card">
            <h3>8. NAT (Network Address Translation)</h3>
            <p>Permet d'économiser les adresses IPv4 en faisant partager une unique adresse IP publique à l'ensemble des équipements d'un réseau privé.</p>
        </div>
    </div>

    <div id="cli" class="content">
        <div class="card">
            <h3>🖥️ Terminal de commande simulé</h3>
            <p>Commandes disponibles : <code>help</code>, <code>ping [ip]</code>, <code>ipconfig</code>, <code>traceroute [hôte]</code>, <code>nslookup [domaine]</code>, <code>clear</code>.</p>
            <div class="terminal" id="termOutput">
                <div>Bienvenue dans la console réseau v1.2.</div>
                <div>Tapez 'help' pour afficher la liste des commandes.</div>
            </div>
            <div class="terminal-input-container">
                <input type="text" id="termInput" style="flex:1;" placeholder="Saisissez votre commande..." onkeydown="if(event.key==='Enter') execCmd()">
                <button class="btn" onclick="execCmd()">Exécuter</button>
            </div>
        </div>
    </div>

    <div id="outils" class="content">
        <div class="card">
            <h3>🧮 Calculateur de Sous-Réseau CIDR</h3>
            <p>Saisissez une adresse IPv4 avec son CIDR (ex: <code>192.168.1.100/26</code>) :</p><br>
            <input type="text" id="cidrInput" value="192.168.1.100/26">
            <button class="btn" onclick="analyserCIDR()">Analyser</button>
            <pre id="cidrOutput">En attente de calcul...</pre>
        </div>
    </div>

    <div id="exercices" class="content">
        <div class="card">
            <h3>✏️ Exercices pratiques</h3>
            <div class="exo-box">
                <h4>1. Étapes DHCP</h4>
                <p>Quelles sont les 4 étapes du protocole DHCP désignées par l'acronyme DORA ?</p>
                <button class="btn btn-secondary" onclick="toggleExo(1)">Voir la réponse</button>
                <div id="exoAns1" style="display:none; margin-top:10px;">
                    Discover, Offer, Request, Acknowledge.
                </div>
            </div>
            <div class="exo-box">
                <h4>2. Sous-réseau (/27)</h4>
                <p>Combien d'hôtes utilisables contient un sous-réseau en /27 ?</p>
                <button class="btn btn-secondary" onclick="toggleExo(2)">Voir la réponse</button>
                <div id="exoAns2" style="display:none; margin-top:10px;">
                    32 - 27 = 5 bits hôtes -> 2⁵ - 2 = 30 hôtes utilisables.
                </div>
            </div>
        </div>
    </div>

    <div id="quiz" class="content">
        <div class="card">
            <h3>🧠 Évaluation rapide</h3>
            <div class="quiz-question">
                <p>1. Quel protocole assure une connexion fiable avec un mécanisme de type Three-Way Handshake ?</p>
                <label><input type="radio" name="qz1" value="a"> UDP</label>
                <label><input type="radio" name="qz1" value="b"> TCP</label>
                <label><input type="radio" name="qz1" value="c"> IP</label>
            </div>
            <div class="quiz-question">
                <p>2. Quel service traduit un nom de domaine (ex: google.com) en adresse IP ?</p>
                <label><input type="radio" name="qz2" value="a"> DHCP</label>
                <label><input type="radio" name="qz2" value="b"> NAT</label>
                <label><input type="radio" name="qz2" value="c"> DNS</label>
            </div>
            <button class="btn" onclick="evalQuiz()">Soumettre</button>
            <div id="quizScore" class="score-box"></div>
        </div>
    </div>
</div>

<script>
    function toggleTheme() {
        const body = document.body;
        const currentTheme = body.getAttribute('data-theme');
        const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
        body.setAttribute('data-theme', newTheme);
        document.querySelector('.theme-toggle').textContent = newTheme === 'dark' ? '☀️ Mode Clair' : '🌙 Mode Sombre';
    }

    document.querySelectorAll('.tab').forEach(tab => {
        tab.addEventListener('click', function() {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.content').forEach(c => c.classList.remove('active'));
            this.classList.add('active');
            document.getElementById(this.dataset.tab).classList.add('active');
        });
    });

    function execCmd() {
        const input = document.getElementById('termInput');
        const output = document.getElementById('termOutput');
        const cmd = input.value.trim();
        if (!cmd) return;

        const line = document.createElement('div');
        line.textContent = '> ' + cmd;
        line.style.color = '#38bdf8';
        output.appendChild(line);

        const parts = cmd.split(' ');
        const mainCmd = parts[0].toLowerCase();
        const arg = parts[1] || '';

        const res = document.createElement('div');
        res.style.marginBottom = "8px";

        switch (mainCmd) {
            case 'help':
                res.textContent = "Commandes : ping [ip], ipconfig, traceroute [hôte], nslookup [domaine], clear, help";
                break;
            case 'ping':
                res.textContent = arg ? `Envoi de paquets vers ${arg}...\nRéponse : temps=12ms TTL=56\n0% de perte.` : "Usage: ping <ip>";
                break;
            case 'ipconfig':
                res.textContent = "IP : 192.168.1.45\nMasque : 255.255.255.0\nPasserelle : 192.168.1.1";
                break;
            case 'traceroute':
            case 'tracert':
                res.textContent = arg ? `Itinéraire vers ${arg} :\n  1  1 ms  192.168.1.1\n  2  12 ms ${arg}` : "Usage: traceroute <hôte>";
                break;
            case 'nslookup':
                res.textContent = arg ? `Serveur : local\nNom : ${arg}\nAdresse : 142.250.185.78` : "Usage: nslookup <domaine>";
                break;
            case 'clear':
                output.innerHTML = '';
                input.value = '';
                return;
            default:
                res.textContent = `'${mainCmd}' non reconnu. Tapez 'help'.`;
                res.style.color = '#ef4444';
        }

        output.appendChild(res);
        output.scrollTop = output.scrollHeight;
        input.value = '';
    }

    function analyserCIDR() {
        const val = document.getElementById('cidrInput').value.trim();
        const out = document.getElementById('cidrOutput');
        const match = val.match(/^(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})\/(\d{1,2})$/);

        if (!match) {
            out.textContent = "Erreur : Format requis (ex: 192.168.1.0/24)";
            return;
        }

        const cidr = parseInt(match[2]);
        if (cidr < 0 || cidr > 32) {
            out.textContent = "Erreur : CIDR entre 0 et 32 requis.";
            return;
        }

        const hostBits = 32 - cidr;
        const totalHosts = Math.pow(2, hostBits);
        const usableHosts = hostBits >= 2 ? totalHosts - 2 : (hostBits === 1 ? 0 : 1);

        out.textContent = `--- RÉSULTAT ---\nIP : ${match[1]} /${cidr}\nBits hôtes : ${hostBits}\nCapacité totale : ${totalHosts}\nHôtes utiles : ${usableHosts}`;
    }

    function toggleExo(id) {
        const el = document.getElementById('exoAns' + id);
        el.style.display = el.style.display === 'none' ? 'block' : 'none';
    }

    function evalQuiz() {
        const q1 = document.querySelector('input[name="qz1"]:checked');
        const q2 = document.querySelector('input[name="qz2"]:checked');
        const box = document.getElementById('quizScore');
        box.style.display = 'block';

        let score = 0;
        if (q1 && q1.value === 'b') score++;
        if (q2 && q2.value === 'c') score++;

        box.innerHTML = `Score : <strong>${score} / 2</strong><br>` + 
                        (score === 2 ? "Parfait ! Tout est correct." : "Relisez les sections de cours correspondantes.");
        box.style.background = score === 2 ? "#10b981" : "#f59e0b";
    }
</script>
</body>
</html>
