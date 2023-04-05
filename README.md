# Console-APP-C-Lunch-Order-System
Console APP C++ Lunch Order System
//Ksenia doing part with login a User
// Function to login a user
User *
loginUser ()
{
  string username, password;
  cout << "Enter username: ";
  cin >> username;
  cout << "Enter password: ";
  cin >> password;
for (auto & user:users)
    {
      if (user.username == username && user.password == password)
	{
	  return &user;
	}
    }
  return nullptr;
}

// Function to add a menu item
void
addMenuItem ()
{
  string name;
  double price;
  cout << "Enter item name: ";
  cin >> name;
  cout << "Enter item price: ";
  cin >> price;
  menu[menu.size () + 1] =
  {
  name, price};
}

// Function to remove a menu item
void
removeMenuItem ()
{
  int id;
  cout << "Enter item ID to remove: ";
  cin >> id;
  menu.erase (id);
}

// Function to display the menu
void
displayMenu ()
{
  cout << "Menu:\n";
for (auto &[id, item]:menu)
    {
      cout << id << ". " << item.name << " - $" << item.price << "\n";
    }
}

// Function to place an order
void
placeOrder (User & user)
{
  vector < MenuItem > items;
  while (true)
    {
      displayMenu ();
      int id;
      cout << "Enter item ID to add (0 to finish): ";
      cin >> id;
      if (id == 0)
	{
	  break;
	}
      auto item = menu.find (id);
      if (item != menu.end ())
	{
	  items.push_back (item->second);
	}
    }
