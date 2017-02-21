Your rules go here.
All rule files have to have the ".rules" file extension and must follow a special syntax.

Check out the openHAB documentation for more details:
http://docs.openhab.org/features/automation/ruledsl.html

Actions in Regeln:
https://github.com/openhab/openhab1-addons/wiki/Actions


/****************************************************************************
 *	Cron
 ***************************************************************************/
Tool to create cron expressions:	www.cronmaker.com (leaf seconds)
http://www.quartz-scheduler.org/documentation/quartz-2.1.x/tutorials/tutorial-lesson-06
1. Seconds
2. Minutes
3. Hours
4. Day-of-Month
5. Month
6. Day-of-Week
7. Year (optional field)



/****************************************************************************
 *	Funktionen
 ***************************************************************************/
	- Funktion in Funktion
	  Es gibt einen Fehler wenn eine Funktion aus einer Funktion gerufen wird!
	  Diese Schachtelung ist somit nicht möglich
	- Zugriff auf globale Variablen aus einer Funktion heraus nicht möglich!
	  Globale Variablen in rules sind für Funktionen nicht sichtbar. Somit müssen
	  diese als zusätzliche Parameter übergeben werden.
	  Achtung: die IDE gibt keinen Fehler aus!!!
	           => am besten unterschiedliche Namen verwenden (für global und innerhalb der Funktion)
 
// Zahl ist Anzahl der Parameter, zusätzlich Result typisieren
// keine primitiven Typen als Parameter erleubt
// letzte Zeile ist automatisch Rückgabewert (oder so ähnlich)
var Functions$Function1<Integer, Object> myTestFunc = [
    Integer myNumber |
    	logDebug("bath", "--- juhu --- " +myNumber)
    	void
]


/**
 * Util Funktion um ein Item zu bekommen
 */
var Functions$Function2<String, GroupItem, GenericItem> getItem = [
	String itemname, GroupItem group |
	 	logDebug("bath", "getItem(), itemname=" +itemname+ ", group=" +group.name)
		return group.members.findFirst[name.equals(itemname)] as GenericItem
]

Verwendung:
	var Number target	= getItem.apply(itemBaseName + "_thermostat", group).state as DecimalType
