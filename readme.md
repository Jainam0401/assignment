the Problem is simple we have to assign customer the checkout which has least items

so there are two solutions

I have considered to have minimum 3 checkouts

1. brute force (which I have applied in code)
   time complexity - O(n * m) where n = number of checkouts and m = average number of items per checkout
    Iterates over each checkout and calculates the total using reduce or similar methods each time. This leads to unnecessary recalculations

    
2. optimzed O(n)
   I will attach that solution below
   In this solution we avaoid recalculation(reduce functions)

        checkouts = [[],[],[]]
        checkoutTotal = [0,0,0]


        function getIndex() {
        let minTotal = checkoutTotal[0];
        let selectedIndex = 0;
        for (i = 0; i < checkoutTotal.length; i++) {

                if (checkoutTotal[i] < minTotal) {
                    minTotal = checkoutTotal[i];
                    selectedIndex = i;

                }
                }
                return selectedIndex;
            }

        function additem() {
        if (checkouts.length === 0) {
        alert("Please initialize checkouts first");
        return;
        }
        const index = getIndex();
        const items = Math.floor(Math.random() \* 10) + 1;

            checkouts[index].push(items);
            checkoutTotals[index] += items;
            updateUi();

        }

In a React-based setup, you can optimize further by updating only the UI component associated with the affected checkout (using the returned index from getIndex()), instead of re-rendering the entire component tree.

This logic mimics a load balancer, where the request is routed to the least busy server (checkout in our case).