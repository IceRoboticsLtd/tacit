CREATING NODEJS MODULES

See also https://quickleft.com/blog/creating-and-publishing-a-node-js-module/

Requirements:
- Have NodeJS installed on your computer (default at /usr/local/bin). See http://coolestguidesontheplanet.com/installing-node-js-osx-10-9-mavericks/
- Make sure you have the latest version and /usr/local/bin is in your $PATH. To upgrade, run: [sudo] npm install npm -g

Configure npm

Type the following:

npm set init.author.name "Willem van Heemstra"
npm set init.author.email "willem@vanheemstrasystems.com"
npm set init.author.url "http://vanheemstrasystems.com"

This next command will prompt you for an email and password, create or verify a user in the npm registry, and save the credentials to the ~/.npmrc file. If you are already added, but forgotten your password, go to https://www.npmjs.com/forgot

Type the following (as root):

npm adduser

P.S. I choose the following credentials:
Username: wvanheemstra
Password: ********
Email: (this IS public) willem@vanheemstrasystems.com
