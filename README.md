// ==UserScript==
// @name         Yandex Bot
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       Borodin Ilya
// @match        https://yandex.ru/*
// @icon         data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==
// @grant        none
// ==/UserScript==
let keywords = ["Автомобили с пробегом", "Лада Приора 2013 года купить", "Купить автомобиль в Москве"];
let keyword = keywords[getRandom(0, keywords.length)];
let inputClick = document.getElementsByClassName("mini-suggest__input")[0];
let yandexInput = document.getElementsByClassName("mini-suggest__input")[0];
let buttonClick = document.getElementsByClassName("search2__button")[0].click();

let links = document.links;

if (inputClick !== undefined) {
inputClick.click();
yandexInput.value = keyword;
} else {

for (let i = 0; i < links.length; i++) {
    if (links[i].href.includes("auto.ru")) {
    let link = links[i];
    console.log ("Find " + links[i]);
    link.click();
    break;
    }
}
}
function getRandom (min, max) {
    return Math.floor(Math.random()*(max - min) + min);
}
