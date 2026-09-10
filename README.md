# Console Pokémon Battle Game Engine
**Team Members**

* **Bouchikhi Shareefah** (Student ID: 23123508)
* **Chelsea Choo Minshe** (Student ID: 24008252)
* **Fatima Abdullah** (Student ID: 24135667)
* **Lee Jia Yue Janice** (Student ID: 24002404)
* **Teo Wan Yin** (Student ID: 23136039)
* **Thanesh Sridharan** (Student ID: 22000798)


**UML Class Diagram & Relationships**

The core application logic and structural breakdown are modeled around an interactive Pokémon battle game.

Diagram Asset URL: [Google Drive Link](https://drive.google.com/file/d/12wjD-mlg4LVvCIIKOXS2Sc-ISkG83M6u/view?usp=sharing)

* **`Game`**
  * **Role:** Central controller managing the battle flow, round execution, player actions, wild Pokémon generation, and menu navigation.
  * **Relationships:** Holds direct associations with `Player`, `ScoreManager`, `Inventory`, and `Pokemon` instances.

* **`Player`**
  * **Role:** Represents the human user, storing team composition, current score, and personal inventory.
  * **Relationships:** Aggregates a list of `Pokemon` objects (0 to 6) and owns 1 `Inventory` instance.

* **`Pokemon`**
  * **Role:** Encapsulates stats (HP, attack power, speed, base values), type mechanics, and battle state alterations.
  * **Relationships:** Uses `TypeEffectiveness` for damage calculations during attacks.

* **`Item` (Abstract Superclass)**
  * **Role:** Defines standard interface properties (`getName()`, `getDescription()`, `use()`) for all usable inventory items.
  * **Relationships:** Inherited by `Pokeballs`, `BoxingGloves`, and `Boots`.

* **`Inventory`**
  * **Role:** Stores and manages collected items for the player.
  * **Relationships:** Contains a list of `Item` objects.

* **`TypeEffectiveness` & `ScoreManager`**
  * **Role:** Utility components providing type matchup multipliers and persistent high-score tracking via file standard output.


**Add-on Features Description & Justifications**

* **Inventory System**
  * **Description:** An overall storage and retrieval framework allowing players to view, select, and utilize items such as Pokeballs and Boosters dynamically during battle.
  * **Justification & OOP Concepts:** Introduces strategic resource management mirroring official Pokémon game mechanics. Demonstrates Encapsulation through private item collections, Inheritance via sub-item specialization, and Polymorphism by invoking `use()` generically on `Item` references.

* **Boxing Gloves (Booster Subclass)**
  * **Description:** A specific battle item extending `Item` that grants a temporary +10 attack power boost to the active Pokémon for one turn.
  * **Justification & OOP Concepts:** Demonstrates explicit Inheritance and Polymorphism by overriding `getName()`, `getDescription()`, and `use()`. Encapsulates temporary stat-boosting arithmetic safely within the class scope.

* **Boots (Booster Subclass)**
  * **Description:** A battle item extending `Item` that provides a temporary +10 speed boost for one turn, altering turn order priority in combat.
  * **Justification & OOP Concepts:** Implements the Single Responsibility Principle by decoupling speed mechanics from attack boosters while utilizing shared parent interfaces.

* **Boosters Utility Class**
  * **Description:** Provides centralized static methods (`getAttackBoost()`, `getSpeedBoost()`, `getDescription()`) using safe string constants and switch logic.
  * **Justification & OOP Concepts:** Ensures high modularity, scalability, and clean code reuse by preventing repetitive boost value initializations across item instances.
