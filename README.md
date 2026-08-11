<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Cours complet et gratuit sur les réseaux informatiques avec schémas, exemples interactifs, exercices et quiz.">
    <title>Apprendre le Réseau - Cours complet & Pratique</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Arial, sans-serif; background: #f0f4f8; padding: 20px; color: #333; line-height: 1.65; }
        .container { max-width: 1040px; margin: auto; background: white; border-radius: 14px; padding: 28px; box-shadow: 0 6px 20px rgba(0,0,0,0.08); }
        h1 { color: #1a3c6e; margin-bottom: 6px; font-size: 1.9rem; }
        .subtitle { color: #555; margin-bottom: 22px; }
        
        /* Navigation par onglets */
        .tabs { display: flex; gap: 10px; margin: 22px 0 18px; flex-wrap: wrap; border-bottom: 2px solid #e5eaf0; padding-bottom: 12px; }
        .tab { padding: 11px 20px; background: #e8eef5; border: none; border-radius: 8px; cursor: pointer; font-weight: 600; color: #1a3c6e; transition: 0.2s; }
        .tab.active { background: #1a3c6e; color: white; }
        .tab:hover:not(.active) { background: #d0dbe8; }
        
        .content { display: none; padding: 8px 0; }
        .content.active { display: block; }
        
        /* Cartes & Blocs */
        .card { background: #f8fafc; border-left: 5px solid #1a3c6e; padding: 18px 20px; margin: 16px 0; border-radius: 0 10px 10px 0; }
        .card h3 { color: #1a3c6e; margin-bottom: 10px; font-size: 1.25rem; }
        .card h4 { color: #2c5282; margin: 16px 0 7px; font-size: 1.08rem; }
        .card ul, .card ol { margin-left: 22px; margin-top: 6px; }
        .card li { margin-bottom: 5px; }
        
        .highlight { background: #e8f0fe; padding: 12px 15px; border-radius: 8px; margin: 12px 0; border-left: 4px solid #3b82f6; }
        .warning { background: #fef3c7; padding: 12px 15px; border-radius: 8px; margin: 12px 0; border-left: 4px solid #f59e0b; }
        .schema-box { background: #f1f5f9; border: 1px solid #cbd5e1; border-radius: 10px; padding: 15px; margin: 15px 0; text-align: center; overflow-x: auto; }
        
        pre { background: #1e1e1e; color: #f8f8f2; padding: 14px; border-radius: 8px; overflow-x: auto; margin: 10px 0; font-size: 0.93rem; }
        code { font-family: Consolas, Monaco, monospace; }
        
        /* Boutons & Champs */
        .btn { padding: 10px 18px; background: #1a3c6e; color: white; border: none; border-radius: 7px; cursor: pointer; margin: 5px 3px 5px 0; font-weight: 500; transition: 0.2s; }
        .btn:hover { background: #14305a; }
        .btn-secondary { background: #64748b; }
        .btn-secondary:hover { background: #475569; }
        input[type="text"] { padding: 9px 12px; border: 1px solid #cbd5e1; border-radius: 6px; width: 210px; max-width: 100%; font-size: 1rem; }
        
        /* Tableaux */
        table { width: 100%; border-collapse: collapse; margin: 12px 0; font-size: 0.94rem; }
        th, td { border: 1px solid #d1d5db; padding: 9px 11px; text-align: left; }
        th { background: #1a3c6e; color: white; }
        tr:nth-child(even) { background: #f8fafc; }
        
        /* Quiz & Exercices */
        .quiz-question { margin: 16px 0; padding: 16px; background: #f1f5f9; border-radius: 10px; }
        .quiz-question p { font-weight: 600; margin-bottom: 8px; }
        .quiz-options label { display: block; margin: 6px 0; cursor: pointer; }
        .score-box { background: #1a3c6e; color: white; padding: 16px; border-radius: 10px; text-align: center; margin-top: 20px; font-size: 1.15rem; display: none; }
        .exo-box { background: #fff7ed; border-left: 5px solid #f97316; padding: 16px; margin: 14px 0; border-radius: 0 10px 10px 0; }
        .exo-box h4 { color: #c2410c; margin-bottom: 8px; }
        
        /* Sommaire */
        .toc { background: #f1f5f9; padding: 14px 18px; border-radius: 10px; margin-bottom: 20px; }
        .toc a { display: inline-block; color: #1a3c6e; text-decoration: none; margin: 3px 8px 3px 0; font-size: 0.93rem; font-weight: 500; }
        .toc a:hover { text-decoration: underline; }
        
        /* Styles RJ45 & Cable */
        .wire-list { list-style: none !important; margin-left: 0 !important; }
        .wire-item { padding: 6px 12px; margin: 4px 0; border-radius: 4px; font-weight: bold; color: #fff; text-shadow: 0 1px 2px rgba(0,0,0,0.6); display: flex; align-items: center; justify-content: space-between; }
        .wire-1 { background: linear-gradient(90deg, #ffffff 50%, #ff7700 50%); color: #000; text-shadow: none; border: 1px solid #ccc; }
        .wire-2 { background: #ff7700; }
        .wire-3 { background: linear-gradient(90deg, #ffffff 50%, #00aa00 50%); color: #000; text-shadow: none; border: 1px solid #ccc; }
        .wire-4 { background: #0066cc; }
        .wire-5 { background: linear-gradient(90deg, #ffffff 50%, #0066cc 50%); color: #000; text-shadow: none; border: 1px solid #ccc; }
        .wire-6 { background: #00aa00; }
        .wire-7 { background: linear-gradient(90deg, #ffffff 50%, #8b4513 50%); color: #000; text-shadow: none; border: 1px solid #ccc; }
        .wire-8 { background: #8b4513; }

        @media (max-width: 600px) { .container { padding: 16px; } h1 { font-size: 1.5rem; } input[type="text"] { width: 100%; } }
    </style>
</head>
<body>
<div class="container">
    <h1>📡 Apprendre le Réseau & le Sertissage</h1>
    <p class="subtitle">Cours théorique + sertissage RJ45 + outils interactifs + exercices + quiz</p>

    <div class="tabs">
        <button class="tab active" data-tab="cours">📘 Cours</button>
        <button class="tab" data-tab="sertissage">🛠️ Sertissage RJ45</button>
        <button class="tab" data-tab="exemples">⚡ Exemples & Outils</button>
        <button class="tab" data-tab="exercices">✏️ Exercices</button>
        <button class="tab" data-tab="quiz">🧠 Quiz</button>
    </div>

    <div id="cours" class="content active">
        <div class="toc">
            <strong>Accès rapide :</strong><br>
            <a href="#intro">1. Intro</a> |
            <a href="#osi">2. Modèle OSI</a> |
            <a href="#tcpip">3. TCP/IP</a> |
            <a href="#adressage">4. IPv4 / IPv6</a> |
            <a href="#subnetting">5. Subnetting</a> |
            <a href="#tcp">6. TCP / UDP</a> |
            <a href="#dhcp-dns">7. DHCP & DNS</a> |
            <a href="#nat">8. NAT</a> |
            <a href="#vlan">9. VLAN</a> |
            <a href="#routage">10. Routage</a> |
            <a href="#switching">11. Switching</a> |
            <a href="#securite">12. Sécurité</a> |
            <a href="#commandes">13. Commandes CLI</a>
        </div>

        <div class="card" id="intro">
            <h3>1. Introduction aux réseaux</h3>
            <p>Un réseau informatique permet à des appareils d’échanger des données et de partager des ressources.</p>
            <table>
                <tr><th>Type</th><th>Étendue</th><th>Exemple</th></tr>
                <tr><td>PAN</td><td>Très courte (quelques mètres)</td><td>Bluetooth (casque, montre)</td></tr>
                <tr><td>LAN</td><td>Local (bâtiment, maison)</td><td>Réseau d'entreprise, Wi-Fi domestique</td></tr>
                <tr><td>MAN</td><td>Ville / Campus</td><td>Réseau métropolitain de fibre</td></tr>
                <tr><td>WAN</td><td>Mondial</td><td>Internet</td></tr>
            </table>
        </div>

        <div class="card" id="osi">
            <h3>2. Le modèle OSI (7 couches)</h3>
            <div class="schema-box">
                <svg width="380" height="260" viewBox="0 0 380 260">
                    <rect x="40" y="5" width="300" height="28" rx="4" fill="#7c3aed"/><text x="190" y="24" fill="white" text-anchor="middle" font-size="13" font-weight="bold">7 - Application</text>
                    <rect x="40" y="39" width="300" height="28" rx="4" fill="#6d28d9"/><text x="190" y="58" fill="white" text-anchor="middle" font-size="13">6 - Présentation</text>
                    <rect x="40" y="73" width="300" height="28" rx="4" fill="#5b21b6"/><text x="190" y="92" fill="white" text-anchor="middle" font-size="13">5 - Session</text>
                    <rect x="40" y="107" width="300" height="28" rx="4" fill="#1d4ed8"/><text x="190" y="126" fill="white" text-anchor="middle" font-size="13">4 - Transport</text>
                    <rect x="40" y="141" width="300" height="28" rx="4" fill="#1e40af"/><text x="190" y="160" fill="white" text-anchor="middle" font-size="13">3 - Réseau</text>
                    <rect x="40" y="175" width="300" height="28" rx="4" fill="#1e3a8a"/><text x="190" y="194" fill="white" text-anchor="middle" font-size="13">2 - Liaison de données</text>
                    <rect x="40" y="209" width="300" height="28" rx="4" fill="#172554"/><text x="190" y="228" fill="white" text-anchor="middle" font-size="13">1 - Physique</text>
                </svg>
            </div>
            <div class="highlight">Moyen mnémotechnique : <strong>« Aucun Problème Si Tu Révises La Physique »</strong></div>
        </div>

        <div class="card" id="tcpip">
            <h3>3. Le modèle TCP/IP</h3>
            <ul>
                <li><strong>Application</strong> → HTTP, HTTPS, DNS, FTP, SMTP</li>
                <li><strong>Transport</strong> → TCP / UDP</li>
                <li><strong>Internet</strong> → IP, ICMP, ARP</li>
                <li><strong>Accès réseau</strong> → Ethernet, Wi-Fi</li>
            </ul>
        </div>

        <div class="card" id="adressage">
            <h3>4. Adressage IPv4 et IPv6</h3>
            <h4>IPv4 (32 bits - décimal pointé)</h4>
            <pre>Adresse IP     : 192.168.1.10
Masque         : 255.255.255.0 (/24)
Réseau         : 192.168.1.0
Broadcast      : 192.168.1.255
Hôtes possibles: 254</pre>
            <h4>IPv6 (128 bits - hexadécimal)</h4>
            <p>Exemple : <code>2001:0db8:85a3:0000:0000:8a2e:0370:7334</code> (ou <code>2001:db8:85a3::8a2e:370:7334</code>)</p>
        </div>

        <div class="card" id="subnetting">
            <h3>5. Subnetting (Découpage de réseaux)</h3>
            <p>Le subnetting divise un grand réseau en plusieurs sous-réseaux plus petits pour optimiser l'organisation et la sécurité.</p>
            <h4>Exemple : découper 192.168.1.0/24 en 4 sous-réseaux</h4>
            <pre>On emprunte 2 bits d'hôte → Masque /26

Sous-réseau 1 : 192.168.1.0/26   (Hôtes: .1 à .62 | Broadrast: .63)
Sous-réseau 2 : 192.168.1.64/26  (Hôtes: .65 à .126 | Broadcast: .127)
Sous-réseau 3 : 192.168.1.128/26 (Hôtes: .129 à .190 | Broadcast: .191)
Sous-réseau 4 : 192.168.1.192/26 (Hôtes: .193 à .254 | Broadcast: .255)</pre>
            <div class="highlight">
                Formules : <strong>Nombre de sous-réseaux = 2ⁿ</strong> (n = bits empruntés)<br>
                <strong>Hôtes utilisables = 2ʰ - 2</strong> (h = bits hôtes restants)
            </div>
        </div>

        <div class="card" id="tcp">
            <h3>6. TCP vs UDP</h3>
            <p><strong>TCP</strong> est fiable, vérifie la réception et établit une connexion (*Three-Way Handshake*).</p>
            <pre>Client ---- SYN ----> Serveur
Client <--- SYN+ACK --- Serveur
Client ---- ACK ----> Serveur (Connexion établie)</pre>
            <div class="warning"><strong>UDP</strong> est non orienté connexion : rapide, sans contrôle de livraison (parfait pour le streaming, la voix sur IP et le jeu vidéo).</div>
        </div>

        <div class="card" id="dhcp-dns">
            <h3>7. DHCP et DNS</h3>
            <h4>DHCP (Dynamic Host Configuration Protocol)</h4>
            <p>Attribue automatiquement la configuration IP (DORA) :</p>
            <pre>1. Discover    → Le client cherche un serveur DHCP (Broadcast)
2. Offer       → Le serveur propose une IP
3. Request     → Le client confirme la demande d'IP
4. Acknowledge → Le serveur valide le bail</pre>
            <h4>DNS (Domain Name System)</h4>
            <p>Annuaire d'Internet traduisant les noms de domaine en adresses IP (ex: <code>google.com</code> → <code>142.250.185.78</code>).</p>
        </div>

        <div class="card" id="nat">
            <h3>8. NAT (Network Address Translation)</h3>
            <p>Permet d'économiser les adresses IPv4 en faisant partager une unique adresse IP publique à l'ensemble des équipements d'un réseau privé.</p>
        </div>

        <div class="card" id="vlan">
            <h3>9. VLAN (Virtual LAN)</h3>
            <p>Sépare logiquement un réseau physique sur un même switch afin de renforcer la sécurité et de réduire la diffusion (broadcast).</p>
        </div>

        <div class="card" id="routage">
            <h3>10. Routage</h3>
            <table>
                <tr><th>Type</th><th>Avantages</th><th>Inconvénients</th></tr>
                <tr><td>Statique</td><td>Sécurisé, pas de surcharge CPU</td><td>Inadapté aux grands réseaux</td></tr>
                <tr><td>Dynamique (OSPF, BGP)</td><td>S'adapte automatiquement aux pannes</td><td>Consomme des ressources</td></tr>
            </table>
        </div>

        <div class="card" id="switching">
            <h3>11. Commutation (Switching)</h3>
            <p>Le switch fonctionne à la <strong>Couche 2 (Liaison)</strong>. Il utilise une table d'adresses MAC pour acheminer les trames uniquement au destinataire désigné, contrairement au Hub qui réémet sur tous les ports.</p>
        </div>

        <div class="card" id="securite">
            <h3>12. Sécurité réseau de base</h3>
            <ul>
                <li><strong>Firewall (Pare-feu)</strong> : Filtre le trafic entrant et sortant selon des règles.</li>
                <li><strong>ACL (Access Control List)</strong> : Listes d'autorisations/refus appliquées sur les routeurs.</li>
                <li><strong>VPN (Virtual Private Network)</strong> : Chiffre la communication sur un réseau public.</li>
            </ul>
        </div>

        <div class="card" id="commandes">
            <h3>13. Commandes réseau indispensables</h3>
            <table>
                <tr><th>Commande</th><th>Rôle</th></tr>
                <tr><td><code>ping</code></td><td>Vérifie la connectivité réseau vers un hôte</td></tr>
                <tr><td><code>ipconfig</code> (Win) / <code>ip a</code> (Linux)</td><td>Affiche les adresses IP et cartes réseau</td></tr>
                <tr><td><code>tracert</code> (Win) / <code>traceroute</code> (Linux)</td><td>Affiche la route (sauts) vers une destination</td></tr>
                <tr><td><code>nslookup</code></td><td>Interroge les serveurs DNS</td></tr>
                <tr><td><code>arp -a</code></td><td>Affiche la table de correspondance IP/MAC</td></tr>
            </table>
        </div>
    </div>

    <div id="sertissage" class="content">
        <div class="card">
            <h3>🛠️ Guide Pratique : Sertir un câble réseau RJ45</h3>
            <p>Sertir un câble Ethernet à paires torsadées permet de fabriquer ou réparer un câble droit ou croisé.</p>
            
            <h4>Matériel requis :</h4>
            <ul>
                <li>Câble réseau (Cat 5e, Cat 6, UTP/STP)</li>
                <li>Connecteurs RJ45 mâles</li>
                <li>Pince à sertir RJ45</li>
                <li>Dénudeur de câble ou ciseaux de précision</li>
                <li>Testeur de câble (optionnel mais conseillé)</li>
            </ul>

            <h4 style="margin-top:15px;">Norme T568B (Standard Câble Droit)</h4>
            <p>En tenant le connecteur RJ45 avec la <strong>languette/clip plastique tournée vers le bas</strong>, placez les fils dans cet ordre exact de gauche à droite :</p>
            
            <ul class="wire-list" style="margin-top:10px;">
                <li class="wire-item wire-1"><span>1. Blanc / Orange</span><span>Broche 1</span></li>
                <li class="wire-item wire-2"><span>2. Orange</span><span>Broche 2</span></li>
                <li class="wire-item wire-3"><span>3. Blanc / Vert</span><span>Broche 3</span></li>
                <li class="wire-item wire-4"><span>4. Bleu</span><span>Broche 4</span></li>
                <li class="wire-item wire-5"><span>5. Blanc / Bleu</span><span>Broche 5</span></li>
                <li class="wire-item wire-6"><span>6. Vert</span><span>Broche 6</span></li>
                <li class="wire-item wire-7"><span>7. Blanc / Marron</span><span>Broche 7</span></li>
                <li class="wire-item wire-8"><span>8. Marron</span><span>Broche 8</span></li>
            </ul>

            <h4 style="margin-top:20px;">Procédure étape par étape :</h4>
            <ol>
                <li><strong>Dénuder :</strong> Retirer environ 2,5 cm de la gaine extérieure sans entailler la protection des petits brins.</li>
                <li><strong>Détorsader :</strong> Séparer et aligner à plat les 8 brins.</li>
                <li><strong>Ordonner :</strong> Classer les brins selon le code couleur <strong>T568B</strong>.</li>
                <li><strong>Couper droit :</strong> Couper les brins bien alignés à environ 1,2 cm de la gaine.</li>
                <li><strong>Insérer :</strong> Glisser les brins à fond dans le connecteur RJ45 jusqu'à voir le cuivre au bout du connecteur. La gaine extérieure doit pénétrer légèrement dans la fiche.</li>
                <li><strong>Sertir :</strong> Insérer le connecteur dans la pince à sertir et presser fermement.</li>
            </ol>
        </div>
    </div>

    <div id="exemples" class="content">
        <div class="card">
            <h3>📡 Simulation Ping</h3>
            <input type="text" id="pingInput" value="8.8.8.8">
            <button class="btn" onclick="simulerPing()">Lancer le Ping</button>
            <pre id="pingResult">Résultat de la commande...</pre>
        </div>

        <div class="card">
            <h3>🌐 Conversion IP → Binaire</h3>
            <input type="text" id="ipBinInput" value="192.168.1.1">
            <button class="btn" onclick="convertirIP()">Convertir</button>
            <pre id="ipBinResult">Cliquez sur convertir...</pre>
        </div>

        <div class="card">
            <h3>🧮 Calculateur de sous-réseau rapide</h3>
            <p>Entrez une adresse avec notation CIDR (ex: 192.168.1.0/26)</p>
            <input type="text" id="subnetInput" value="192.168.1.0/26" style="width:260px;">
            <button class="btn" onclick="calculerSubnet()">Calculer</button>
            <pre id="subnetResult">Résultat du calcul...</pre>
        </div>

        <div class="card">
            <h3>🔌 Testeur de Câble RJ45 Simulé</h3>
            <p>Simulez le test de continuité des 8 brins d'un câble serti :</p>
            <button class="btn" onclick="testerCable(true)">Tester câble parfait</button>
            <button class="btn btn-secondary" onclick="testerCable(false)">Tester câble défectueux</button>
            <pre id="cableTesterResult">Appuyez sur un bouton pour tester...</pre>
        </div>
    </div>

    <div id="exercices" class="content">
        <div class="card">
            <h3>✏️ Exercices pratiques</h3>

            <div class="exo-box">
                <h4>Exercice 1 – Identifier le réseau</h4>
                <p>Soit l'IP <strong>172.16.5.40</strong> avec le masque <strong>255.255.0.0 (/16)</strong>.</p>
                <ol>
                    <li>Quelle est l'adresse réseau ?</li>
                    <li>Quelle est l'adresse de Broadcast ?</li>
                    <li>Combien d'hôtes utilisables ce réseau comporte-t-il ?</li>
                </ol>
                <button class="btn btn-secondary" onclick="toggleCorrection(1)">Afficher la correction</button>
                <div id="corr1" style="display:none;margin-top:10px;padding:12px;background:#ecfdf5;border-radius:8px;">
                    1. Adresse réseau : <strong>172.16.0.0</strong><br>
                    2. Broadcast : <strong>172.16.255.255</strong><br>
                    3. Nombre d'hôtes : 2¹⁶ - 2 = <strong>65 534 hôtes</strong>
                </div>
            </div>

            <div class="exo-box">
                <h4>Exercice 2 – Subnetting</h4>
                <p>Découpez le réseau <strong>192.168.10.0/24</strong> en 4 sous-réseaux égaux. Donnez leur masque et leurs adresses réseau.</p>
                <button class="btn btn-secondary" onclick="toggleCorrection(2)">Afficher la correction</button>
                <div id="corr2" style="display:none;margin-top:10px;padding:12px;background:#ecfdf5;border-radius:8px;">
                    Masque : <strong>/26 (255.255.255.192)</strong><br>
                    - SR 1 : 192.168.10.0/26<br>
                    - SR 2 : 192.168.10.64/26<br>
                    - SR 3 : 192.168.10.128/26<br>
                    - SR 4 : 192.168.10.192/26
                </div>
            </div>

            <div class="exo-box">
                <h4>Exercice 3 – TCP ou UDP ?</h4>
                <p>Associez le bon protocole de transport :</p>
                <ol>
                    <li>Téléchargement d'un logiciel via HTTPS</li>
                    <li>Appel vocal Discord (VoIP)</li>
                    <li>Envoi d'un e-mail (SMTP)</li>
                </ol>
                <button class="btn btn-secondary" onclick="toggleCorrection(3)">Afficher la correction</button>
                <div id="corr3" style="display:none;margin-top:10px;padding:12px;background:#ecfdf5;border-radius:8px;">
                    1. <strong>TCP</strong> (Exige l'intégrité parfaite du fichier)<br>
                    2. <strong>UDP</strong> (Privilégie la vitesse et la faible latence)<br>
                    3. <strong>TCP</strong> (Nécessite une remise garantie)
                </div>
            </div>
        </div>
    </div>

    <div id="quiz" class="content">
        <div class="card">
            <h3>🧠 Quiz de validation des connaissances (12 questions)</h3>

            <div class="quiz-question"><p>1. Quel protocole associe une adresse IP à une adresse physique MAC ?</p>
                <label><input type="radio" name="q1" value="a"> DNS</label>
                <label><input type="radio" name="q1" value="b"> ARP</label>
                <label><input type="radio" name="q1" value="c"> DHCP</label>
            </div>

            <div class="quiz-question"><p>2. Quelle est la taille d'une adresse IPv4 en bits ?</p>
                <label><input type="radio" name="q2" value="a"> 16 bits</label>
                <label><input type="radio" name="q2" value="b"> 32 bits</label>
                <label><input type="radio" name="q2" value="c"> 128 bits</label>
            </div>

            <div class="quiz-question"><p>3. À quelle couche du modèle OSI se situe le routage des paquets ?</p>
                <label><input type="radio" name="q3" value="a"> Couche 4 - Transport</label>
                <label><input type="radio" name="q3" value="b"> Couche 3 - Réseau</label>
                <label><input type="radio" name="q3" value="c"> Couche 2 - Liaison</label>
            </div>

            <div class="quiz-question"><p>4. Quel service attribue automatiquement une configuration IP aux hôtes ?</p>
                <label><input type="radio" name="q4" value="a"> DNS</label>
                <label><input type="radio" name="q4" value="b"> DHCP</label>
                <label><input type="radio" name="q4" value="c"> NAT</label>
            </div>

            <div class="quiz-question"><p>5. Quelle est la particularité majeure du protocole TCP ?</p>
                <label><input type="radio" name="q5" value="a"> Il privilégie la vitesse sans contrôle d'erreurs</label>
                <label><input type="radio" name="q5" value="b"> Il est fiable et orienté connexion</label>
                <label><input type="radio" name="q5" value="c"> Il s'utilise uniquement sans fil</label>
            </div>

            <div class="quiz-question"><p>6. Selon la norme T568B pour RJ45, quelle est la couleur du brin N°1 ?</p>
                <label><input type="radio" name="q6" value="a"> Vert</label>
                <label><input type="radio" name="q6" value="b"> Blanc / Orange</label>
                <label><input type="radio" name="q6" value="c"> Blanc / Vert</label>
            </div>

            <div class="quiz-question"><p>7. Combien d'hôtes utilisables contient un sous-réseau en /26 ?</p>
                <label><input type="radio" name="q7" value="a"> 62</label>
                <label><input type="radio" name="q7" value="b"> 64</label>
                <label><input type="radio" name="q7" value="c"> 126</label>
            </div>

            <div class="quiz-question"><p>8. Quelles sont les 4 étapes du processus DHCP ?</p>
                <label><input type="radio" name="q8" value="a"> DORA (Discover, Offer, Request, Acknowledge)</label>
                <label><input type="radio" name="q8" value="b"> PING (Packet, Internet, Network, Gateway)</label>
                <label><input type="radio" name="q8" value="c"> INIT (Init, Network, IP, Terminal)</label>
            </div>

            <div class="quiz-question"><p>9. À quelle couche fonctionne principalement un Commutateur (Switch) classique ?</p>
                <label><input type="radio" name="q9" value="a"> Couche 3</label>
                <label><input type="radio" name="q9" value="b"> Couche 2</label>
                <label><input type="radio" name="q9" value="c"> Couche 1</label>
            </div>

            <div class="quiz-question"><p>10. Quel protocole est directement exploité par la commande `ping` ?</p>
                <label><input type="radio" name="q10" value="a"> TCP</label>
                <label><input type="radio" name="q10" value="b"> ICMP</label>
                <label><input type="radio" name="q10" value="c"> UDP</label>
            </div>

            <div class="quiz-question"><p>11. Qu'est-ce que le Three-Way Handshake (SYN, SYN-ACK, ACK) ?</p>
                <label><input type="radio" name="q11" value="a"> Un échange pour fermer un VLAN</label>
                <label><input type="radio" name="q11" value="b"> La négociation d'établissement de connexion TCP</label>
                <label><input type="radio" name="q11" value="c"> Un protocole de chiffrement Wi-Fi</label>
            </div>

            <div class="quiz-question"><p>12. Quel est le rôle principal d'un VLAN ?</p>
                <label><input type="radio" name="q12" value="a"> Augmenter le débit de la ligne fibre</label>
                <label><input type="radio" name="q12" value="b"> Séparer logiquement des réseaux sur un même switch</label>
                <label><input type="radio" name="q12" value="c"> Remplacer le serveur DNS</label>
            </div>

            <button class="btn" onclick="calculerScore()" style="margin-top:15px;">Valider mes réponses</button>
            <div id="scoreFinal" class="score-box"></div>
        </div>
    </div>
</div>

<script>
    // Navigation Onglets
    document.querySelectorAll('.tab').forEach(tab => {
        tab.addEventListener('click', function() {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.content').forEach(c => c.classList.remove('active'));
            this.classList.add('active');
            document.getElementById(this.dataset.tab).classList.add('active');
        });
    });

    // Outil Simulation Ping
    function simulerPing() {
        const ip = document.getElementById('pingInput').value.trim();
        const result = document.getElementById('pingResult');
        if (!ip) { result.textContent = 'Veuillez saisir une IP.'; return; }
        const d = Math.floor(Math.random() * 40 + 10);
        result.textContent = `Envoi d'une requête Ping sur ${ip} avec 32 octets de données :
Réponse de ${ip} : octets=32 temps=${d}ms TTL=118
Réponse de ${ip} : octets=32 temps=${d+2}ms TTL=118
Réponse de ${ip} : octets=32 temps=${d-1}ms TTL=118

Statistiques Ping :
    Paquets : envoyés = 3, reçus = 3, perdus = 0 (perte 0%)`;
    }

    // Outil Conversion IP -> Binaire
    function convertirIP() {
        const ip = document.getElementById('ipBinInput').value.trim();
        const result = document.getElementById('ipBinResult');
        const octets = ip.split('.');
        if (octets.length !== 4) { result.textContent = 'Format invalide (ex: 192.168.1.1)'; return; }
        let ok = true;
        const bin = octets.map(o => {
            const n = parseInt(o, 10);
            if (isNaN(n) || n < 0 || n > 255) { ok = false; return 'ERR'; }
            return n.toString(2).padStart(8, '0');
        }).join(' . ');
        result.textContent = ok ? `${ip}\n→ ${bin}` : 'Octet invalide (doit être compris entre 0 et 255)';
    }

    // Outil Subnetting
    function calculerSubnet() {
        const input = document.getElementById('subnetInput').value.trim();
        const result = document.getElementById('subnetResult');
        const match = input.match(/^(\d+\.\d+\.\d+\.\d+)\/(\d+)$/);
        if (!match) { result.textContent = 'Format attendu : 192.168.1.0/26'; return; }
        
        const cidr = parseInt(match[2], 10);
        if (cidr < 0 || cidr > 32) { result.textContent = 'CIDR invalide (0 à 32)'; return; }
        
        const hostBits = 32 - cidr;
        const hosts = hostBits >= 2 ? (Math.pow(2, hostBits)) - 2 : 0;
        
        result.textContent = `Analyse CIDR : /${cidr}
Bits consacrés aux hôtes : ${hostBits}
Nombre d'hôtes utilisables : ${hosts}`;
    }

    // Outil Testeur de câble
    function testerCable(parfait) {
        const result = document.getElementById('cableTesterResult');
        if (parfait) {
            result.textContent = `Testeur de câble connecté...
PIN 1: [OK]  PIN 2: [OK]  PIN 3: [OK]  PIN 4: [OK]
PIN 5: [OK]  PIN 6: [OK]  PIN 7: [OK]  PIN 8: [OK]
RÉSULTAT : Câble conforme (T568B OK)`;
        } else {
            result.textContent = `Testeur de câble connecté...
PIN 1: [OK]  PIN 2: [OK]  PIN 3: [ERR - Faux contact]
PIN 4: [OK]  PIN 5: [OK]  PIN 6: [ERR - Inversé]
PIN 7: [OK]  PIN 8: [OK]
RÉSULTAT : Câble défectueux - À resertir !`;
        }
    }

    // Affichage des corrections d'exercices
    function toggleCorrection(num) {
        const el = document.getElementById('corr' + num);
        el.style.display = el.style.display === 'none' ? 'block' : 'none';
    }

    // Calculateur de score Quiz
    function calculerScore() {
        const answers = { q1:'b', q2:'b', q3:'b', q4:'b', q5:'b', q6:'b', q7:'a', q8:'a', q9:'b', q10:'b', q11:'b', q12:'b' };
        let score = 0;
        for (let q in answers) {
            const sel = document.querySelector(`input[name="${q}"]:checked`);
            if (sel && sel.value === answers[q]) score++;
        }
        const box = document.getElementById('scoreFinal');
        box.style.display = 'block';
        let msg = score === 12 ? 'Parfait ! Tu maîtrises parfaitement le sujet 🎉' :
                  score >= 9 ? 'Très bon travail ! Les notions clés sont acquises.' :
                  score >= 6 ? 'Résultat correct, relis certaines sections pour consolidert.' : 
                  'N\'hésite pas à revoir le cours et refaire le quiz !';
        box.innerHTML = `Ton score : <strong>${score} / 12</strong><br>${msg}`;
    }
</script>
</body>
</html>
