# to check if the number is even or odd
function oddeven(num) {
    if (num % 2 === 0) {
        console.log(num + " is Even");
    } else {
        console.log(num + " is Odd");
    }
}

oddeven(27);

# to calculate grades
function grades(marks) {
    if (marks >= 80){
        console.log("its A GRADE")
    }
    else if (marks >= 70){
        console.log("its B GRADE")
    }
    else if (marks >= 60){
        console.log("its C GRADE")
    }
    else if (marks >= 50){
        console.log("its D GRADE")
    }
    else if (marks >= 40){
        console.log("its E GRADE")
    }
    else if (marks >= 30){
        console.log("its F GRADE")
    }
}
grades(68)
# calculating total number of vowels and reversing a string
function countVowelsAndReverseString(word) {
    let count = 0;

    for (let i = 0; i < word.length; i++) {
        if (
            word[i] === "a" ||
            word[i] === "e" ||
            word[i] === "i" ||
            word[i] === "o" ||
            word[i] === "u"
        ) {
            count++;
        }
    }

    console.log("Vowels:", count);

    let reversed = word.split("").reverse().join("");
    console.log("Reversed String:", reversed);
}

countVowelsAndReverseString("javascript");

