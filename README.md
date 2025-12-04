# Canteen-menu-management--C
#include <stdio.h>

struct Canteen {
    char dish[30];
    int price;
    char counter[30];
};

void findCounter(struct Canteen menu[], char input[]) {
    int i, j, same, found = 0;

   for (i = 0; i < 5; i++) {
        same = 1;
        for (j = 0; input[j] != '\0' || menu[i].dish[j] != '\0'; j++) {
            if (input[j] != menu[i].dish[j]) {
                same = 0;
                break;
            }
        }

  if (same == 1) {
            printf("\n--- Details Found ---\n");
            printf("Dish Name: %s\n", menu[i].dish);
            printf("Price: %d\n", menu[i].price);
            printf("Counter Location: %s\n", menu[i].counter);
            found = 1;
            break;
        }
    }

   if (found == 0) {
        printf("\nDish not found in any counter.\n");
    }
}

int main() {
    struct Canteen menu[5] = {
        {"Masala_Dosa", 80, "Counter_1_South_Indian"},
        {"Veg_Burger", 120, "Counter_2_Fast_Food"},
        {"Hakka_Noodles", 150, "Counter_3_Chinese"},
        {"Pav_Bhaji", 100, "Counter_4_Chat_Center"},
        {"Red_Pasta", 200, "Counter_5_Italian"}
    };

  char input[30];
    int i;
    printf("=== TODAY'S MENU ===\n");
    for(i = 0; i < 5; i++) {
        printf("%d. %s\n", i + 1, menu[i].dish);
    }
    printf("====================\n");

  printf("\nEnter dish name exactly from the menu above: ");
    scanf("%s", input);

  findCounter(menu, input);

   return 0;
}

