Lern-Periode 3
Finn Holle

9.1.2024 bis 30.1.2024 (☃️ Sportferien)

Grob-Planung
Ich habe im Modul 431 eine sehr gute Note bekommen und in 319 ein mittelmässige Note? In Modul 431 war ich besonders stark. Für mich ist 319 besonders wichtig da ich dort am meisten mühe hatte?
Am Ende der LP2 habe ich mir vorgenommen das ich mehr Routine bekomme und mir schneller neue Funktionen aneignen kann. Mein VBV war das ich mich nicht von andern ablenken lasse. In dem ich mich auf meine Arbeit konzentrire.
Ein geeignetes Projekt für diese LP3 ist ein Trainingsplangenerator?
9.1.2024
✍️ Heute habe ich... (50-100 Wörter)

16.1 und 23.1.2024
- [x] Namen, Alter und Geschlechtseingabe erstellen
- [x] Herausfinden wie sich das Ziel auf Trainingsmenge und Intensität auswirkt/ Herausfinden was für Trainigsaufteilungen in Verschiedenen Ambitionen gebraucht werden
- [ ] Eine Zielauswahl definieren und diese Implementieren
- [x] Eine Intensitätsauswahl festlegen und diese Implementieren

Testfall-Nummer	Ausgangslage (Given)	Eingabe (When)	Ausgabe (Then)	Erfüllt?
1	Man kann Namen eingeben / Leandro / Was ist ihr alter?
2 Man kann sein Alter eingeben / 16 / Was ist ihr Geschlecht
3 Man kann ein Ziel auswählen / fitter werden / nächste Auswahl
4 Man kann eine Intensität des Trainings auswählen/ intensiv / nächste Auswahl
			
✍️ Heute am 16.1 habe ich... (50-100 Wörter)

☝️ Vergessen Sie nicht, bis zum 16.1 einen ersten Code auf github hochzuladen, und in der Spalte Erfüllt? einzutragen, ob Ihr Code die Test-Fälle erfüllt

23.1.2024
- [x] Eine Aufwandsauswahl definieren und einfügen
- [x] Verschiedene Trainingsmethoden einfügen
- [ ] Wochenzuteilung erstellen
- [ ] Ergebnistest implementieren



Testfall-Nummer	Ausgangslage (Given)	Eingabe (When)	Ausgabe (Then)	Erfüllt?
5	Man kann die Aufwandsauswahl abgeben / 10 / Trainingsplan
6 Gib deine alte FTP an / 231 / Watt pro Kilo
7 Gib deine neue FTP an / 254 / Watt pro Kilo Fortschritt in Prozent
✍️ Heute am 23.1 habe ich... (50-100 Wörter)
Heute habe ich eine Aufwandsauswahl definiert von Leicht, Mittel zu Hoch. Man kann angeben zu wie viel Aufwand man bereit ist. Ich habe gelernt strukturiert zu coden.
☝️ Vergessen Sie nicht, bis zum 23.1 Ihren fixfertigen Code auf github hochzuladen, und in der Spalte Erfüllt? einzutragen, ob Ihr Code die Test-Fälle erfüllt

30.1.2024
✍️ Heute am 23.1 habe ich... (50-100 Wörter

namespace Trainingsplan
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string name = Eingabe("Gib deinen Namen ein:");
            int alter = IntEingabe("Gib dein Alter ein:");
            string geschlecht = Eingabe("Gib dein Geschlecht ein (m/w):");

            Ziel ziel = ZielAuswahl();
            Intensität intensität = IntensitätsAuswahl();
            Aufwand aufwand = AufwandAuswahl();

            List<string> trainingsplan = ErstelleTrainingsplan(ziel, intensität, aufwand);

            Console.WriteLine($"\nTrainingsplan für {name}, {alter} Jahre, Geschlecht: {geschlecht}, Ziel: {ziel}, Intensität: {intensität}, Aufwand: {aufwand}");
            foreach (var einheit in trainingsplan)
            {
                Console.WriteLine(einheit);
            }

            Ergebnistest(trainingsplan);
        }

        static string Eingabe(string prompt)
        {
            Console.WriteLine(prompt);
            return Console.ReadLine();
        }

        static int IntEingabe(string prompt)
        {
            Console.WriteLine(prompt);
            return Convert.ToInt32(Console.ReadLine());
        }

        static Ziel ZielAuswahl()
        {
            Console.WriteLine("\nWähle dein Trainingsziel:");
            Console.WriteLine("1. Muskelaufbau");
            Console.WriteLine("2. Fettverbrennung");
            Console.WriteLine("3. Allgemeine Fitness");

            int auswahl = IntEingabe("Gib die Nummer deines Ziels ein:");

            switch (auswahl)
            {
                case 1:
                    return Ziel.Muskelaufbau;
                case 2:
                    return Ziel.Fettverbrennung;
                case 3:
                    return Ziel.AllgemeineFitness;
                default:
                    Console.WriteLine("Ungültige Auswahl. Standardziel Allgemeine Fitness wird verwendet.");
                    return Ziel.AllgemeineFitness;
            }
        }

        static Intensität IntensitätsAuswahl()
        {
            Console.WriteLine("\nWähle deine Trainingsintensität:");
            Console.WriteLine("1. Leicht");
            Console.WriteLine("2. Mittel");
            Console.WriteLine("3. Schwer");

            int auswahl = IntEingabe("Gib die Nummer deiner Intensität ein:");

            switch (auswahl)
            {
                case 1:
                    return Intensität.Leicht;
                case 2:
                    return Intensität.Mittel;
                case 3:
                    return Intensität.Schwer;
                default:
                    Console.WriteLine("Ungültige Auswahl. Standardintensität Mittel wird verwendet.");
                    return Intensität.Mittel;
            }
        }

        static Aufwand AufwandAuswahl()
        {
            Console.WriteLine("\nWähle deinen Trainingsaufwand:");
            Console.WriteLine("1. Gering");
            Console.WriteLine("2. Normal");
            Console.WriteLine("3. Hoch");

            int auswahl = IntEingabe("Gib die Nummer deines Aufwands ein:");

            switch (auswahl)
            {
                case 1:
                    return Aufwand.Gering;
                case 2:
                    return Aufwand.Normal;
                case 3:
                    return Aufwand.Hoch;
                default:
                    Console.WriteLine("Ungültige Auswahl. Standardaufwand Normal wird verwendet.");
                    return Aufwand.Normal;
            }
        }

        static List<string> ErstelleTrainingsplan(Ziel ziel, Intensität intensität, Aufwand aufwand)
        {
            List<string> trainingsplan = new List<string>();

            switch (ziel)
            {
                case Ziel.Muskelaufbau:
                    trainingsplan.Add("Fahrradtraining - Intervallfahren, 5 Intervalle an 3 Minuten schnelles Fahren, gefolgt von 2 Minuten langsameres Fahren");
                    trainingsplan.Add("Fahrradtraining - Dauerfahrt, 30 Minuten moderates Tempo");
                    break;
                case Ziel.Fettverbrennung:
                    trainingsplan.Add("Fahrradtraining - Dauerfahrt, 45 Minuten moderates Tempo");
                    trainingsplan.Add("Fahrradtraining - Intervallfahren, 4 Intervalle an 4 Minuten schnelles Fahren, gefolgt von 2 Minuten langsameres Fahren");
                    break;
                case Ziel.AllgemeineFitness:
                    trainingsplan.Add("Fahrradtraining - Dauerfahrt, 20 Minuten moderates Tempo");
                    trainingsplan.Add("Fahrradtraining - Bergfahrt, 3 Anstiege an 5 Minuten");
                    break;
                default:
                    break;
            }

            switch (intensität)
            {
                case Intensität.Leicht:
                    // Anpassungen für leicht
                    break;
                case Intensität.Mittel:
                    // Standardintensität
                    break;
                case Intensität.Schwer:
                    // Anpassungen für schwer
                    break;
                default:
                    break;
            }

            switch (aufwand)
            {
                case Aufwand.Gering:
                    // Anpassungen für geringen Aufwand
                    break;
                case Aufwand.Normal:
                    // Standardaufwand
                    break;
                case Aufwand.Hoch:
                    // Anpassungen für hohen Aufwand
                    break;
                default:
                    break;
            }

            return trainingsplan;
        }

        static void Ergebnistest(List<string> trainingsplan)
        {
            // Hier könntest du einen einfachen Ergebnistest durchführen
            Console.WriteLine("\nErgebnistest:");
            Console.WriteLine("Du hast den Trainingsplan erhalten. Überprüfe deine Fortschritte nach einigen Wochen.");
        }
    }

    enum Ziel
    {
        Muskelaufbau,
        Fettverbrennung,
        AllgemeineFitness
    }

    enum Intensität
    {
        Leicht,
        Mittel,
        Schwer
    }

    enum Aufwand
    {
        Gering,
        Normal,
        Hoch
    }
}
    


Reflexion
Formen Sie Ihre Zusammenfassungen in Hinblick auf Ihren VBV zu einem zusammenhängenden Text von 100 bis 200 Wörtern (wieder mit Angabe in Klammern).

Verfassen Sie zusätzlich einen kurzen Abschnitt, in welchem Sie über die Länge der Projekte reflektieren: Fanden Sie die 9-wöchtige LP2 oder die 4-wöchige LP3 angenehmer? Was bedeutet das für Ihre Planung der zukünftigen LP?
