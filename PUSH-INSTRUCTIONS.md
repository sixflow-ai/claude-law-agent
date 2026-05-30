# How to publish this marketplace to GitHub

You run these (I can't push to your GitHub for you). Replace SixFlowAI with your GitHub
account/org if different.

1. Create a new EMPTY repo on GitHub named: sixflow-marketplace
   (Public is fine; private also works if your clients' Cowork can access it.)

2. From inside this folder:

   git init
   git add .
   git commit -m "SixFlow marketplace: law-firm-ops plugin"
   git branch -M main
   git remote add origin https://github.com/SixFlowAI/sixflow-marketplace.git
   git push -u origin main

3. Clients install in Cowork with:

   /plugin marketplace add SixFlowAI/sixflow-marketplace
   /plugin install sixflow-law-firm-ops@sixflow

4. To ship updates later: edit the plugin files, bump the version in
   plugins/sixflow-law-firm-ops/.claude-plugin/plugin.json, commit, and push.
   Clients refresh with:  /plugin marketplace update

Note: sixflow-clientgen (the /plugin-custom generator) is INTERNAL - it is intentionally
NOT in this client marketplace. Keep it in a separate private repo or install it locally.
