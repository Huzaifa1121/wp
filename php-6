<?php

// Page created by Shepard [Fabian Pijcke] <Shepard8@laposte.net>
// Arno Esterhuizen <arno.esterhuizen@gmail.com>
// and Romain Bourdon <rromain@romainbourdon.com>
// and Hervé Leclerc <herve.leclerc@alterway.fr>
// Icons by Mark James <http://www.famfamfam.com/lab/icons/silk/>
// Version 2.5 -> 3.0.0 by Dominique Ottello aka Otomatic
// 3.1.9 - Support VirtualHost IDNA ServerName
//
//
//

$server_dir = "../";

require $server_dir.'scripts/config.inc.php';
require $server_dir.'scripts/wampserver.lib.php';

//chemin jusqu'aux fichiers alias
$aliasDir = $server_dir.'alias/';

//Fonctionne à condition d'avoir ServerSignature On et ServerTokens Full dans httpd.conf
$server_software = $_SERVER['SERVER_SOFTWARE'];
$error_content = '';

// on récupère les versions des applis
$phpVersion = $wampConf['phpVersion'];
$apacheVersion = $wampConf['apacheVersion'];
$doca_version = 'doca'.substr($apacheVersion,0,3);
$mysqlVersion = $wampConf['mysqlVersion'];

//On récupére la valeur de urlAddLocalhost
$suppress_localhost = ($wampConf['urlAddLocalhost'] == 'off' ? true : false);

//On récupère la valeur de VirtualHostMenu
$VirtualHostMenu = $wampConf['VirtualHostSubMenu'];

//on récupère la valeur de apachePortUsed
$port = $wampConf['apachePortUsed'];
$UrlPort = $port !== "80" ? ":".$port : '';
//On récupère le ou les valeurs des ports en écoute dans Apache
$ListenPorts = implode(' - ',listen_ports());
//on récupère la valeur de mysqlPortUsed
$Mysqlport = $wampConf['mysqlPortUsed'];


// répertoires à ignorer dans les projets
$projectsListIgnore = array ('.','..','wampthemes','wamplangues');

// Recherche des différents thèmes disponibles
$styleswitcher = '<select id="themes">'."\n";
$themes = glob('wampthemes/*', GLOB_ONLYDIR);
foreach ($themes as $theme) {
    if (file_exists($theme.'/style.css')) {
        $theme = str_replace('wampthemes/', '', $theme);
        $styleswitcher .= '<option id="'.$theme.'">'.$theme.'</option>'."\n";
    }
