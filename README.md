Timelyx – Version Netlify (IA + Stripe + PayPal)

 Ajouter les clés Stripe / PayPal sur Netlify

Aller dans :

Site settings → Environment variables

Ajouter :

STRIPE_SECRET_KEY=sk_live_xxxxxxxxxxxxxxxxxxxx
STRIPE_PRICE_ID=price_xxxxxxxx
PAYPAL_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
PAYPAL_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Puis cliquer Save → Restart build.


---

🧩 Structure du projet

timelyx/
│
├── index.html
├── success.html
├── cancel.html
├── style.css
├── timelyx-ai.js
│
├── payments/
│   ├── stripe.js
│   └── paypal.js
│
├── netlify.toml
│
└── netlify/
    └── functions/
        ├── create-checkout-session.js
        ├── stripe-webhook.js
        ├── paypal-create.js
        └── paypal-capture.js


---

💳 Paiements intégrés

Stripe

Utilise :

create-checkout-session.js

stripe-webhook.js


Ce flux :

1. Crée une session Stripe Checkout


2. Redirige l’utilisateur


3. Webhook reçoit confirmation


4. Active l’accès IA




---

PayPal

Utilise :

paypal-create.js

paypal-capture.js


Process :

1. Génération d’un ordre PayPal


2. Paiement


3. Capture du paiement


4. Redirection vers /success.html




---

🤖 Fonction IA

Le fichier :

timelyx-ai.js

Contient l’appel de base à l’agent Timelyx.
Tu peux y connecter :

OpenAI Assistants API

DeepSeek

Gemini

Ton backend maison



---

✔️ Pages importantes

Page	Fonction

/	Page d’accueil / lancement IA / boutons de paiement
/success.html	Paiement validé
/cancel.html	Paiement annulé



---

📦 Configuration Netlify

netlify.toml configure :

Répertoire du site

Répertoire des fonctions

Redirection SPA


Exemple :

[build]
  publish = "."

[functions]
  directory = "netlify/functions"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200


---

🧪 Tester en local

Installer netlify-cli :

npm install -g netlify-cli

Démarrer :

netlify dev


---

📄 Licence

Projet privé • Tous droits réservés © Timelyx



