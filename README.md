# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return; // O(1)
    else {
        mystery(n / 3); // T(n/3)
        var count = 0; // O(1)
        mystery(n / 3); // T(n/3)
        for(var i = 0; i < n*n; i++) { // runs n^2 times
            for(var j = 0; j < n; j++) { // runs n times
                for(var k = 0; k < n*n; k++) { // runs n^2 times
                    count = count + 1; // O(n^2 * n * n^2) = O(n^5)
                }
            }
        }
        mystery(n / 3); // T(n/3)
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Recurrence relation: T(n) = 3T(n/3) + n^5.  To solve the recurrence relation, I used the substitution method.  Before I determined the general case, the problem looked like this: 3^4T(n/3^4) + 3^3(n/3^3)^5 + 3^2(n/3^2)^5 + 3(n/3)^5 + n^5.  Since the problem above consisted of a geometric series, I was led to the general case of: 3^i * T(n/3^i) + n^5 * ((1/3^4)^(i+1)-1)/(3^4-1).  To solve the general case, I determined that i = log3(n) and plugged that into the equation.  After plugging i into the general case, the simplified form was n + n/(8081) - 81n^5/(80 * 81).  Using the simplified form, I came to the conclusion that the runtime for the function is \$Theta(n^5)$ since n^5 grows the fastest and constants can be ignored.

ChatGPT helped correct my analysis of the separate lines of code, as I originally didn't have the right runtime for the recursive lines.  It also helped me simplify the general case when I plugged i into the equation.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models.  All of the work is my own, except where stated otherwise.  I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

-----

I submitted this assignment last semester.
