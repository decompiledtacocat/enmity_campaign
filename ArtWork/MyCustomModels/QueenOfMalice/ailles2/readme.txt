###########################################################################
README

Auteur : Clotaire

Date : 05/2003

Type de model : Arme [] | Equipement [x] | Unité []

Source : http://www.metalplanet.org

Type d'animation: Birth []  | Death [] | Decay [] | Spell [] | Walk [] | Attack [] | Stand [] | Stand Victory []

Chemin du BLP : ailles2.mdx

MDL : Présent [x] | Absent []

Commentaire : Aucun commentaire

############################################################################
                                  MODE D EMPLOIE

ARME OU EQUIPEMENT :

Si vous voulez attacher le model à une unité, il suffi d'ajouter cette action : 

-action : Special Effect - Create Special Effect On Unit
		
	  Special Effect. Create a special effect attached to (Membre où le model doit être attaché) of (NOM DE LA CIBLE) using (MODEL DU ZIP).mdx

------------------------------------------

UNITE :

Outils nécessaires :
- UMS 3.6 ou supérieur
- Winmpq

Sous l'éditeur UMS :
	- Ouvrir l'éditeur d'unité
	- Pour modifier le model de l'unité choisit, il suffit de changer le chemin du MDX dans la ligne Model
	- Le chemin du nouveau MDX est arbitraire, il doit quand même partir du répertoire racine de Warcraft 3, 
		Exemple : Units\model\monmodel.mdx
	- Une fois ce changement fait, enregistrez la map.

Sous Winmpq :
	- Ouvrez la map dernièrement enregistrée
	- Déplacez simplement en faisant cliquer/glisser le MDX et le BLP correspondant au model
	- A ce moment Winmpq vous demandera un chemin, entrez le même chemin mis dans l'éditeur
		Gardons le même exemple : Units\model\
		NE METTEZ PAS LE NOM DU FICHIER DANS LE CHEMIN

#############################################################################

. : : http://www.metalplanet.org : : .
