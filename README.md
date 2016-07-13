# 1

    class Contact //imagine a contact card
    {

        //Three entries on the card. Allocated area on each card:

        public string name;
        public string number;
        public string address;

        public Contact(string name, string number, string address)
        {
            this.name = name;
            this.number = number;
            this.address = address;

            // use "this." to qualify the fields, name and alias

        }

    }
    
     class PhoneBook
    {
        List<Contact> contacts; //array list that has a contact card full of contacts

        public PhoneBook()
        {
            contacts = new List<Contact>(); //New
        }

        public bool addContact(string name, string number, string address)
        {
            Contact card = new Contact(name, number, address);
            Contact show = searchContact(name);

            if( show == null)
            {
                contacts.Add(card);
                return true;
            }
            else
            {
                return false;
            }
            
        }

        public bool deleteContact(string name)
        {
            Contact card = searchContact(name);

            if( card != null)
            {
                contacts.Remove(card);
                return true;
            }
            else
            {
                return false;
            }
        }

        public bool isEmpty()
        {
            return (contacts.Count == 0);
        }

        public void listContact(Action<Contact> list)
        {
            contacts.ForEach(list);
        }

        public Contact searchContact(string name)
        {
            /*Contact card = contacts.Find(delegate (Contact o)
            {
                return o.name == name;
            });
            return card;*/
        }







    } // class phonebook
    
    
     class Program
    {
        PhoneBook book;

        public Program()
        {
            book = new PhoneBook();
        }

        static void Main(string[] args)
        {

            string ownerName;
            string option;
            string start;

            Console.WriteLine("PHONE BOOK \n Enter your first name: ");
            ownerName = Console.ReadLine();
            Console.WriteLine("\nWelcome {0}!", ownerName);

            const string list = "l";
            const string add = "a";
            const string search = "s";
            const string delete = "d";


            Console.WriteLine("Would you like to open or exit your phone book:");
            start = Console.ReadLine();

            while (start != "exit")
            {

                Console.WriteLine("\nHere are your phone book options: \n -L (List all contacts) \n -A (Add new contacts) \n -S (Search contact) \n -D (Delete contact) \nEnter a letter:");

                option = Console.ReadLine();

                switch (option.ToLower())
                {
                    case list:
                        Console.WriteLine("\nHere are your listed contacts(press enter to see all): \n");
                        //listContacts();
                        break;

                    case add:
                        Console.WriteLine("\nAdd a new contact.\n");
                        addContact();
                        break;

                    case search:
                        Console.WriteLine("\nSearch for contact.\n");
                        break;

                    case delete:
                        Console.WriteLine("\nDelete contact.\n");
                        break;

                }

                Console.WriteLine("\nWould you like to open or exit your phone book:");
                start = Console.ReadLine();


                /*  {
                      Console.WriteLine("This is not any of the given options, reselect your letter:\n");
                  }  */

                // Console.ReadKey();
            }
        } // main
    }
}
    
    
