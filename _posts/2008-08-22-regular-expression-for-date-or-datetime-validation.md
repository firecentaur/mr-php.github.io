---
layout: post
title: Regular Expression for Date or Datetime Validation
tags: [php, regex]
redirect_from:
- /code/regular-expression-for-date-or-datetime-validation/
---
This Regular Expression will verify if a date is a valid YYYY-MM-DD with an optional HH:MM:SS.  It checks to see if the day is a valid day in the given month with the consideration of leap years.

<!--break-->

I have created this regex several years ago and now I want to share it with the world.  It is not 100% documented however I have posted output from RegexBuddy's document function.

```php
<?php
if (preg_match('/\\A(?:^((\\d{2}(([02468][048])|([13579][26]))[\\-\\/\\s]?((((0?[13578])|(1[02]))[\\-\\/\\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\\-\\/\\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\\-\\/\\s]?((0?[1-9])|([1-2][0-9])))))|(\\d{2}(([02468][1235679])|([13579][01345789]))[\\-\\/\\s]?((((0?[13578])|(1[02]))[\\-\\/\\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\\-\\/\\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\\-\\/\\s]?((0?[1-9])|(1[0-9])|(2[0-8]))))))(\\s(((0?[0-9])|(1[0-9])|(2[0-3]))\\:([0-5][0-9])((\\s)|(\\:([0-5][0-9])))?))?$)\\z/', $date)) {
	// date is valid
} else {
	// date is invalid
}
```

```
// ^((\d{2}(([02468][048])|([13579][26]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))))|(\d{2}(([02468][1235679])|([13579][01345789]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8]))))))(\s(((0?[0-9])|(1[0-9])|(2[0-3]))\:([0-5][0-9])((\s)|(\:([0-5][0-9])))?))?$
// 
// Assert position at the start of the string «^»
// Match the regular expression below and capture its match into backreference number 1 «((\d{2}(([02468][048])|([13579][26]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))))|(\d{2}(([02468][1235679])|([13579][01345789]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8]))))))»
//    Match either the regular expression below (attempting the next alternative only if this one fails) «(\d{2}(([02468][048])|([13579][26]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))))»
//       Match the regular expression below and capture its match into backreference number 2 «(\d{2}(([02468][048])|([13579][26]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))))»
//          Match a single digit 0..9 «\d{2}»
//             Exactly 2 times «{2}»
//          Match the regular expression below and capture its match into backreference number 3 «(([02468][048])|([13579][26]))»
//             Match either the regular expression below (attempting the next alternative only if this one fails) «([02468][048])»
//                Match the regular expression below and capture its match into backreference number 4 «([02468][048])»
//                   Match a single character present in the list "02468" «[02468]»
//                   Match a single character present in the list "048" «[048]»
//             Or match regular expression number 2 below (the entire group fails if this one fails to match) «([13579][26])»
//                Match the regular expression below and capture its match into backreference number 5 «([13579][26])»
//                   Match a single character present in the list "13579" «[13579]»
//                   Match a single character present in the list "26" «[26]»
//          Match a single character present in the list below «[\-\/\s]?»
//             Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//             A - character «\-»
//             A / character «\/»
//             Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//          Match the regular expression below and capture its match into backreference number 6 «((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9]))))»
//             Match either the regular expression below (attempting the next alternative only if this one fails) «(((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))»
//                Match the regular expression below and capture its match into backreference number 7 «(((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))»
//                   Match the regular expression below and capture its match into backreference number 8 «((0?[13578])|(1[02]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[13578])»
//                         Match the regular expression below and capture its match into backreference number 9 «(0?[13578])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character present in the list "13578" «[13578]»
//                      Or match regular expression number 2 below (the entire group fails if this one fails to match) «(1[02])»
//                         Match the regular expression below and capture its match into backreference number 10 «(1[02])»
//                            Match the character "1" literally «1»
//                            Match a single character present in the list "02" «[02]»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 11 «((0?[1-9])|([1-2][0-9])|(3[01]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 12 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (attempting the next alternative only if this one fails) «([1-2][0-9])»
//                         Match the regular expression below and capture its match into backreference number 13 «([1-2][0-9])»
//                            Match a single character in the range between "1" and "2" «[1-2]»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//                      Or match regular expression number 3 below (the entire group fails if this one fails to match) «(3[01])»
//                         Match the regular expression below and capture its match into backreference number 14 «(3[01])»
//                            Match the character "3" literally «3»
//                            Match a single character present in the list "01" «[01]»
//             Or match regular expression number 2 below (attempting the next alternative only if this one fails) «(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))»
//                Match the regular expression below and capture its match into backreference number 15 «(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))»
//                   Match the regular expression below and capture its match into backreference number 16 «((0?[469])|(11))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[469])»
//                         Match the regular expression below and capture its match into backreference number 17 «(0?[469])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character present in the list "469" «[469]»
//                      Or match regular expression number 2 below (the entire group fails if this one fails to match) «(11)»
//                         Match the regular expression below and capture its match into backreference number 18 «(11)»
//                            Match the characters "11" literally «11»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 19 «((0?[1-9])|([1-2][0-9])|(30))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 20 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (attempting the next alternative only if this one fails) «([1-2][0-9])»
//                         Match the regular expression below and capture its match into backreference number 21 «([1-2][0-9])»
//                            Match a single character in the range between "1" and "2" «[1-2]»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//                      Or match regular expression number 3 below (the entire group fails if this one fails to match) «(30)»
//                         Match the regular expression below and capture its match into backreference number 22 «(30)»
//                            Match the characters "30" literally «30»
//             Or match regular expression number 3 below (the entire group fails if this one fails to match) «(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))»
//                Match the regular expression below and capture its match into backreference number 23 «(0?2[\-\/\s]?((0?[1-9])|([1-2][0-9])))»
//                   Match the character "0" literally «0?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                   Match the character "2" literally «2»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 24 «((0?[1-9])|([1-2][0-9]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 25 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (the entire group fails if this one fails to match) «([1-2][0-9])»
//                         Match the regular expression below and capture its match into backreference number 26 «([1-2][0-9])»
//                            Match a single character in the range between "1" and "2" «[1-2]»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//    Or match regular expression number 2 below (the entire group fails if this one fails to match) «(\d{2}(([02468][1235679])|([13579][01345789]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8])))))»
//       Match the regular expression below and capture its match into backreference number 27 «(\d{2}(([02468][1235679])|([13579][01345789]))[\-\/\s]?((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8])))))»
//          Match a single digit 0..9 «\d{2}»
//             Exactly 2 times «{2}»
//          Match the regular expression below and capture its match into backreference number 28 «(([02468][1235679])|([13579][01345789]))»
//             Match either the regular expression below (attempting the next alternative only if this one fails) «([02468][1235679])»
//                Match the regular expression below and capture its match into backreference number 29 «([02468][1235679])»
//                   Match a single character present in the list "02468" «[02468]»
//                   Match a single character present in the list "1235679" «[1235679]»
//             Or match regular expression number 2 below (the entire group fails if this one fails to match) «([13579][01345789])»
//                Match the regular expression below and capture its match into backreference number 30 «([13579][01345789])»
//                   Match a single character present in the list "13579" «[13579]»
//                   Match a single character present in the list "01345789" «[01345789]»
//          Match a single character present in the list below «[\-\/\s]?»
//             Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//             A - character «\-»
//             A / character «\/»
//             Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//          Match the regular expression below and capture its match into backreference number 31 «((((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))|(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))|(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8]))))»
//             Match either the regular expression below (attempting the next alternative only if this one fails) «(((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))»
//                Match the regular expression below and capture its match into backreference number 32 «(((0?[13578])|(1[02]))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(3[01])))»
//                   Match the regular expression below and capture its match into backreference number 33 «((0?[13578])|(1[02]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[13578])»
//                         Match the regular expression below and capture its match into backreference number 34 «(0?[13578])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character present in the list "13578" «[13578]»
//                      Or match regular expression number 2 below (the entire group fails if this one fails to match) «(1[02])»
//                         Match the regular expression below and capture its match into backreference number 35 «(1[02])»
//                            Match the character "1" literally «1»
//                            Match a single character present in the list "02" «[02]»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 36 «((0?[1-9])|([1-2][0-9])|(3[01]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 37 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (attempting the next alternative only if this one fails) «([1-2][0-9])»
//                         Match the regular expression below and capture its match into backreference number 38 «([1-2][0-9])»
//                            Match a single character in the range between "1" and "2" «[1-2]»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//                      Or match regular expression number 3 below (the entire group fails if this one fails to match) «(3[01])»
//                         Match the regular expression below and capture its match into backreference number 39 «(3[01])»
//                            Match the character "3" literally «3»
//                            Match a single character present in the list "01" «[01]»
//             Or match regular expression number 2 below (attempting the next alternative only if this one fails) «(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))»
//                Match the regular expression below and capture its match into backreference number 40 «(((0?[469])|(11))[\-\/\s]?((0?[1-9])|([1-2][0-9])|(30)))»
//                   Match the regular expression below and capture its match into backreference number 41 «((0?[469])|(11))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[469])»
//                         Match the regular expression below and capture its match into backreference number 42 «(0?[469])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character present in the list "469" «[469]»
//                      Or match regular expression number 2 below (the entire group fails if this one fails to match) «(11)»
//                         Match the regular expression below and capture its match into backreference number 43 «(11)»
//                            Match the characters "11" literally «11»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 44 «((0?[1-9])|([1-2][0-9])|(30))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 45 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (attempting the next alternative only if this one fails) «([1-2][0-9])»
//                         Match the regular expression below and capture its match into backreference number 46 «([1-2][0-9])»
//                            Match a single character in the range between "1" and "2" «[1-2]»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//                      Or match regular expression number 3 below (the entire group fails if this one fails to match) «(30)»
//                         Match the regular expression below and capture its match into backreference number 47 «(30)»
//                            Match the characters "30" literally «30»
//             Or match regular expression number 3 below (the entire group fails if this one fails to match) «(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8])))»
//                Match the regular expression below and capture its match into backreference number 48 «(0?2[\-\/\s]?((0?[1-9])|(1[0-9])|(2[0-8])))»
//                   Match the character "0" literally «0?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                   Match the character "2" literally «2»
//                   Match a single character present in the list below «[\-\/\s]?»
//                      Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                      A - character «\-»
//                      A / character «\/»
//                      Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//                   Match the regular expression below and capture its match into backreference number 49 «((0?[1-9])|(1[0-9])|(2[0-8]))»
//                      Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[1-9])»
//                         Match the regular expression below and capture its match into backreference number 50 «(0?[1-9])»
//                            Match the character "0" literally «0?»
//                               Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                            Match a single character in the range between "1" and "9" «[1-9]»
//                      Or match regular expression number 2 below (attempting the next alternative only if this one fails) «(1[0-9])»
//                         Match the regular expression below and capture its match into backreference number 51 «(1[0-9])»
//                            Match the character "1" literally «1»
//                            Match a single character in the range between "0" and "9" «[0-9]»
//                      Or match regular expression number 3 below (the entire group fails if this one fails to match) «(2[0-8])»
//                         Match the regular expression below and capture its match into backreference number 52 «(2[0-8])»
//                            Match the character "2" literally «2»
//                            Match a single character in the range between "0" and "8" «[0-8]»
// Match the regular expression below and capture its match into backreference number 53 «(\s(((0?[0-9])|(1[0-9])|(2[0-3]))\:([0-5][0-9])((\s)|(\:([0-5][0-9])))?))?»
//    Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//    Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//    Match the regular expression below and capture its match into backreference number 54 «(((0?[0-9])|(1[0-9])|(2[0-3]))\:([0-5][0-9])((\s)|(\:([0-5][0-9])))?)»
//       Match the regular expression below and capture its match into backreference number 55 «((0?[0-9])|(1[0-9])|(2[0-3]))»
//          Match either the regular expression below (attempting the next alternative only if this one fails) «(0?[0-9])»
//             Match the regular expression below and capture its match into backreference number 56 «(0?[0-9])»
//                Match the character "0" literally «0?»
//                   Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//                Match a single character in the range between "0" and "9" «[0-9]»
//          Or match regular expression number 2 below (attempting the next alternative only if this one fails) «(1[0-9])»
//             Match the regular expression below and capture its match into backreference number 57 «(1[0-9])»
//                Match the character "1" literally «1»
//                Match a single character in the range between "0" and "9" «[0-9]»
//          Or match regular expression number 3 below (the entire group fails if this one fails to match) «(2[0-3])»
//             Match the regular expression below and capture its match into backreference number 58 «(2[0-3])»
//                Match the character "2" literally «2»
//                Match a single character in the range between "0" and "3" «[0-3]»
//       Match the character ":" literally «\:»
//       Match the regular expression below and capture its match into backreference number 59 «([0-5][0-9])»
//          Match a single character in the range between "0" and "5" «[0-5]»
//          Match a single character in the range between "0" and "9" «[0-9]»
//       Match the regular expression below and capture its match into backreference number 60 «((\s)|(\:([0-5][0-9])))?»
//          Between zero and one times, as many times as possible, giving back as needed (greedy) «?»
//          Match either the regular expression below (attempting the next alternative only if this one fails) «(\s)»
//             Match the regular expression below and capture its match into backreference number 61 «(\s)»
//                Match a single character that is a "whitespace character" (spaces, tabs, line breaks, etc.) «\s»
//          Or match regular expression number 2 below (the entire group fails if this one fails to match) «(\:([0-5][0-9]))»
//             Match the regular expression below and capture its match into backreference number 62 «(\:([0-5][0-9]))»
//                Match the character ":" literally «\:»
//                Match the regular expression below and capture its match into backreference number 63 «([0-5][0-9])»
//                   Match a single character in the range between "0" and "5" «[0-5]»
//                   Match a single character in the range between "0" and "9" «[0-9]»
// Assert position at the end of the string (or before the line break at the end of the string, if any) «$»
```