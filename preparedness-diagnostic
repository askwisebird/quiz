// function to delete results screen - leaving only error screen
function displayError(){
  $('[quiz-result="success-screen"]').remove();
  return
}

// function to delete error screen - leaving only the success screen
function displaySuccess(){
  $('[quiz-result="error-screen"]').remove();
  return
}


// array of text options based on quiz score
const levels = [
  {min: 90, message: "You're in great shape! While there are a few additional actions you can take to make sure you're prepared, you've got all of the basics covered."},
  {min: 60, message: "Above Average: You've got all of the basics covered, but still have a few action items to complete to get prepared."},
  {min: 20, message: "Average: You've gotten the ball rolling, but are missing a few of the basics that will help you get prepared. Check out the checklist below"},
  {min: 0, message: "Below Average: You've got a few more action items to take care of to make sure you're prepared. Check out the checklist below for some of the action items."},
];

// function to display correct quiz text result based on score
function findTextScore(score) {
  for (const {min, message} of levels) {
      if (score >= min) {
        $('[quiz-result="text-score"]').text(message);
          return
      }
  }
  displayError();
}

if(window.location.search){
  const urlParams = new URLSearchParams(window.location.search);
  if(Array.from(urlParams).length == 22){
    displaySuccess();

    //convert string score to int
    let numScore = parseInt(urlParams.get('score'));

    //insert numerical score onto page
    $('[quiz-result="number-score"]').text(numScore);
  
    //insert score description onto page
    findTextScore(numScore)

    //loop through url queries
    for(const [ key, value ] of urlParams){
      //if quiz result for item is not 1 or not 2 for q1
      if (value != 1){
        //delete the action item
      document.getElementById(key).closest(".quiz-result_accordion").remove();
      }
    }
  }
  else{
    displayError();
  }
}
else{
  displayError();
}
