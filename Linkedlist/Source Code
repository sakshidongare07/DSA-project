#include <iostream>
#include <string>
using namespace std;

struct Song
{
    string name, artist;
    int duration;            // in seconds
    Song *next, *prev;
};

Song *head = NULL, *tail = NULL, *current = NULL;

void showSong(Song *s)
{
    cout << s->name << " | " << s->artist << " | "
         << s->duration / 60 << ":" << s->duration % 60 << endl;
}

// Add song at the end
void addSong()
{
    Song *s = new Song;
    cin.ignore();
    cout << "Enter song name: ";
    getline(cin, s->name);
    cout << "Enter artist: ";
    getline(cin, s->artist);
    cout << "Enter duration (in seconds): ";
    cin >> s->duration;
    s->next = NULL;
    s->prev = NULL;

    if (head == NULL)
        head = tail = current = s;
    else
    {
        tail->next = s;
        s->prev = tail;
        tail = s;
    }
    cout << "Song added!\n";
}

// Delete song by name
void deleteSong()
{
    string n;
    cin.ignore();
    cout << "Enter song name to delete: ";
    getline(cin, n);

    Song *t = head;
    while (t != NULL && t->name != n)
        t = t->next;

    if (t == NULL)
    {
        cout << "Song not found!\n";
        return;
    }
    if (t->prev != NULL) t->prev->next = t->next;
    else head = t->next;

    if (t->next != NULL) t->next->prev = t->prev;
    else tail = t->prev;

    if (current == t)
        current = (t->next != NULL) ? t->next : t->prev;

    delete t;
    cout << "Song deleted!\n";
}

// Search song by name
void searchSong()
{
    string n;
    cin.ignore();
    cout << "Enter song name to search: ";
    getline(cin, n);

    Song *t = head;
    while (t != NULL)
    {
        if (t->name == n)
        {
            cout << "Song found: ";
            showSong(t);
            return;
        }
        t = t->next;
    }
    cout << "Song not found!\n";
}

// Display playlist
void displayPlaylist()
{
    if (head == NULL)
    {
        cout << "Playlist is empty!\n";
        return;
    }
    int i = 1;
    for (Song *t = head; t != NULL; t = t->next)
    {
        cout << i++ << ". ";
        showSong(t);
    }
}

void nextSong()
{
    if (current == NULL) cout << "Playlist is empty!\n";
    else if (current->next == NULL) cout << "End of playlist!\n";
    else
    {
        current = current->next;
        cout << "Now playing: ";
        showSong(current);
    }
}

void previousSong()
{
    if (current == NULL) cout << "Playlist is empty!\n";
    else if (current->prev == NULL) cout << "Start of playlist!\n";
    else
    {
        current = current->prev;
        cout << "Now playing: ";
        showSong(current);
    }
}

int main()
{
    int choice;
    cout << "====================================\n";
    cout << "   MUSIC PLAYLIST MANAGEMENT\n";
    cout << "====================================\n";

    do
    {
        cout << "\n1. Add Song\n2. Delete Song\n3. Search Song\n";
        cout << "4. Display Playlist\n5. Next Song\n6. Previous Song\n";
        cout << "7. Exit\nEnter your choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1: addSong(); break;
            case 2: deleteSong(); break;
            case 3: searchSong(); break;
            case 4: displayPlaylist(); break;
            case 5: nextSong(); break;
            case 6: previousSong(); break;
            case 7: cout << "Goodbye!\n"; break;
            default: cout << "Invalid choice! Try again.\n";
        }
    } while (choice != 7);

    return 0;
}
