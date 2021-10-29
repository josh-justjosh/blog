---
show: 'Phantom Radio'
title: 'Phantom Radio'
artwork: Null
mp3: 
people: ['Head of Radio':'Alex Wood','Head of Music':'Anna Alexander','Technical Manager':'Jack Holcombe','Assistant Technical Managers':["Josh Brunning", "Lux O'Neill-Manning"]]
layout: podcast
date: 2021-09-30
categories: live radio
elsewhere: <a href="https://phantom-media.co.uk/phantom-radio/">Phantom Media</a>
roles: "Assistant Technical Manager"
permalink: /phantomradio
artwork: https://pbs.twimg.com/profile_images/915197631269408768/wbOWmwcI_400x400.jpg
---

<div style="text-align: center; margin: 15px 0; padding: 0"><iframe style="width: 75%; height: 60px; border: 0;" src="https://player.shoutca.st/?username=phantommedia"></iframe></div>

<p style="text-align: center;">Phantom radio runs seven days a week broadcasting music around the clock from our Kedleston Road Studios.<br/>We also have live shows every week:</p>

<table>
    <tr>
        <th>Day</th>
        <th>Time</th>
        <th>Show</th>
        <th>With</th>
    </tr>
    <tr>
        <td>Monday</td>
        <td>18:00 - 20:00</td>
        <td>The Alex Wood Show</td>
        <td>Alex Wood</td>
    </tr>
    <tr>
        <td>Wednesday</td>
        <td>15:00 - 17:00</td>
        <td>The SLLET Radio Show</td>
        <td>Josh Brunning, Dan Jellicoe and Guests</td>
    </tr>
    <tr>
        <td>Friday</td>
        <td>16:00 - 18:00</td>
        <td>Drive Time with Jess, Jack and Anna</td>
        <td>Jess Moore, Jack Holcombe and Anna Alexander</td>
    </tr>
</table>
<script>
function sleep(milliseconds) {
  const date = Date.now();
  let currentDate = null;
  do {
    currentDate = Date.now();
  } while (currentDate - date < milliseconds);
}
var getJSON = function(url) {
  return new Promise(function(resolve, reject) {
    var xhr = new XMLHttpRequest();
    xhr.open('get', url, true);
    xhr.responseType = 'json';
    xhr.onload = function() {
      var status = xhr.status;
      if (status == 200) {
        resolve(xhr.response);
      } else {
        reject(status);
      }
    };
    xhr.send();
  });
};
var updateData = function(url) {
    sleep(2000);
    getJSON(url).then(function(data) {
        //alert('Your Json result is:  ' + data.icestats.source.listeners); //you can comment this, i used it to debug
        result.innerText = "Current Listeners: " + data.icestats.source.listeners; //display the result in an HTML element
        console.log(data.icestats.source.listeners)
    }, function(status) { //error detection....
    console.log('Something went wrong.');
    });
}
updateData("https://phantommedia.radioca.st/status-json.xsl")
</script>
<div style="display:flex;justify-content:space-evenly;align-items:center"><div id="result" style="text-align:center; "></div><div><button onclick='updateData("https://phantommedia.radioca.st/status-json.xsl")'>Update</button></div></div>
