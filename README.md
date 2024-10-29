# Introduction to Git and GitHub

## Simple Interest Calculator

A calculator that calculates simple interest given principal, annual rate of interest and time period in years.

```
Input:
   p, principal amount
   t, time period in years
   r, annual rate of interest
Output
   simple interest = p*t*r
```

package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

type Person struct {
	Fname string
	Lname string
}

func main() {

	var data []map[string]string

	var filename string
	fmt.Println("Enter your 'file.txt':")
	fmt.Scan(&filename)

	file, err := os.Open(filename)
	if err != nil {
		fmt.Println("File does not exists!")
		return
	}
	defer file.Close()

	scanner := bufio.NewScanner(file)

	lineNum := 0
	for scanner.Scan() {
		lineNum++

		line := scanner.Text()
		if lineNum == 1 {

			parts := strings.Fields(line)
			fname := parts[0]
			lname := parts[1]
			p1 := Person{Fname: fname, Lname: lname}
			personMap := make(map[string]string)
			personMap["Fname"] = p1.Fname
			personMap["Lname"] = p1.Lname

			data = append(data, personMap)
		}

	}

	fmt.Println(data)

}


_© 2023 XYZ, Inc._
