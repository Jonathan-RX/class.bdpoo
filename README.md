# class.bdpoo
Gestion de base de donnée Mysql "perso"

*Sommaire :*
* [Comment l'utiliser](#comment-lutiliser-)
* [Fonctions](#fonctions-)
	* [Config](#config)
	* [Insert](#insert)
	* [Update](#update)
	* [Get_results](#get_results)
	* [Query](#query)
	* [Get_option](#get_option)
	* [Set_option](#set_option)
	* [Test_connect](#test_connect)
* [License](#license-)
* [Contribuer / Reporter un problème](#contribuer--reporter-un-problème)

*Date : 12/2009*
*Dernière modification : 06/2017 -> Utilisation de Mysqli*

Cette classe à pour but de simplifier l'accès à une base de donnée en utilisant une méthode de programmation proche de celle de wordpress.

## Comment l'utiliser :
Avant de l'utiliser, il convient de définir les variables $host, $login, $password et $basename en fonction de votre serveur et base de donnée.

Script d'exmple :
```php
$mybd = new Bd;
$mybd->config('hote','utilisateur','mot de passe','base de donnée');
$mybd->update('matable', array('info'=>'Mon titre d\'information'), array('info'=>'My info'));
$tables = $mybd->get_results('SELECT * FROM matable');
print_r($tables);
echo '<br /><br />' . $tables[0]->info;
```

## Fonctions :
### Config
```php
$mybd->config('host','utilisatuer','mot_de_passe','base','prefix','table_option');
```
Fonction de configuration, à appeler avec "host", "utilisateur", "mot_de_passe" et "base" de votre configuration.  
Le paramètre "prefix" permet de définir le préfix de vos tables, "table_option" permet de définir la table utilisée par get_option et set_option.
### Insert
```php
$mybd->insert('nom_table', array('clé1'=>'valeur1','clé2'=>'valeur2'));
```
Permet d'insérer une nouvelle entrée dans la base de donnée dans la table "nom_table" avec un tableau.  
Chaque valeur sera insérée dans la clé correspondante. Retourne "true" en cas de réussite ou "false" en cas d'échec.
### Update
```php
$mybd->update('nom_table', array('clé'=>'valeur'), array('clé_where'=>'valeur_where'));
```
Mise à jours d'une entrée avec "clé_where" et "valeur_where" avec "clé" et "valeur" dans la table "nom_table".  
Retourne "true" en cas de succès ou "false" en cas d'échec.
### Get_results
```php
$resultats = $mybd->get_results('Requête');
```
Exécute "Requête" et renvoi le résultat sous la forme d'un objet STD.
Exemple :
```php
$results = $mybd->get_results('SELECT * FROM ma_table WHERE id="50"');
foreach($results as $r){
	echo 'Résultat : ' . $r->valeur . '<br />';
}
```
### Query
```php
$mybd->query('Requête');
```
Exécute la requête passé en paramètre, returne "true" en cas de réussite ou "false" en cas d'échec.
### Get_option
```php
$mybd->get_option('nom_option');
```
Retourne la valeur de l'entrée dans la table des options correspondante à "nom_option".
### Set_option
```php
$mybd->set_option('nom_option', 'valeur');
```
Défini l'option "nom_option" à la valeur "valeur". Retourne "true" en cas de succès ou "false" en cas d'échec.
### Test_connect
```php
$mybd->test_connect('host','utilisateur','mot_de_passe','base');
```
Teste la connexion à la base de donnée "host" avec "utilisateur" et "mot_de_passe" comme identifiant, en sélectionnant la base "base". Retourne "true" en cas de succès et "false" en cas d'échec.

# License
Ce script est disponible sous la license GNU GENERAL PUBLIC LICENSE V3, voir le fichier LICENSE pour plus d'infos

# Contribuer / Reporter un problème
Si vous rencontrez des problèmes ou des bugs, n'hésitez pas à créer une issue, je regarderais votre remontée dès que possible!
Si vous voyez une faille dans ce script, merci de me remonter l'information afin que je corrige le problème.

Pour toute contribution, créez un fork, éditez et soumettez une "pull request".

Merci d'avoir lu ce fichier jusqu'ici ;-)
