class Task:
    def __init__(self, title, description):
        self.title = title
        self.description = description
        self.completed = False

    def __str__(self):
        status = "Terminée" if self.completed else "Non terminée"
        return f"Tâche: {self.title}\nDescription: {self.description}\nStatut: {status}\n"

    def mark_completed(self):
        self.completed = True

    def mark_incomplete(self):
        self.completed = False


class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)
        print(f"Tâche '{task.title}' ajoutée.")

    def remove_task(self, task_title):
        task_to_remove = None
        for task in self.tasks:
            if task.title == task_title:
                task_to_remove = task
                break
        if task_to_remove:
            self.tasks.remove(task_to_remove)
            print(f"Tâche '{task_title}' supprimée.")
        else:
            print(f"Aucune tâche trouvée avec le titre '{task_title}'.")

    def list_tasks(self):
        if not self.tasks:
            print("Aucune tâche dans la liste.")
        else:
            for task in self.tasks:
                print(task)


def main():
    task_manager = TaskManager()

    while True:
        print("\nOptions:")
        print("1. Ajouter une tâche")
        print("2. Supprimer une tâche")
        print("3. Afficher toutes les tâches")
        print("4. Quitter")

        option = input("Choisissez une option (1-4): ")

        if option == '1':
            title = input("Titre de la tâche: ")
            description = input("Description de la tâche: ")
            task = Task(title, description)
            task_manager.add_task(task)

        elif option == '2':
            title = input("Titre de la tâche à supprimer: ")
            task_manager.remove_task(title)

        elif option == '3':
            task_manager.list_tasks()

        elif option == '4':
            print("Merci d'avoir utilisé le gestionnaire de tâches. À bientôt!")
            break

        else:
            print("Option invalide. Veuillez choisir une option entre 1 et 4.")


if __name__ == "__main__":
    main()
