<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Murder at Blackwood Manor | Criminal Law Review</title>
<style>
:root{
  --navy:#101d2c;
  --panel:#1d3044;
  --red:#c8102e;
  --gold:#e8bd70;
  --text:#f5f3ed;
  --muted:#c4d0db;
  --green:#b5edc4;
}
*{box-sizing:border-box}
body{
  margin:0;
  background:var(--navy);
  color:var(--text);
  font-family:Georgia,serif;
  line-height:1.6;
}
button,textarea{font:inherit}
button{
  cursor:pointer;
  border:1px solid var(--gold);
  border-radius:8px;
  padding:12px 17px;
  background:var(--panel);
  color:var(--text);
}
button:hover:not(:disabled){background:#354b62}
button:focus-visible,textarea:focus-visible{
  outline:3px solid #ffcf72;
  outline-offset:3px;
}
button:disabled{opacity:.55;cursor:not-allowed}
.primary{
  background:var(--red);
  border-color:var(--red);
  font-weight:bold;
}
.primary:hover:not(:disabled){background:#a80c27}
header{
  text-align:center;
  padding:38px 16px;
  background:linear-gradient(145deg,#263a4d,#0b1420);
  border-bottom:3px solid var(--red);
}
.eyebrow{
  color:var(--gold);
  letter-spacing:3px;
  font-size:12px;
  text-transform:uppercase;
}
h1{
  font-size:clamp(28px,5vw,48px);
  line-height:1.15;
  margin:12px 0;
}
h2{color:var(--gold);line-height:1.3}
h3{color:var(--gold)}
.subtitle{color:var(--muted)}
main{max-width:1050px;margin:auto;padding:22px}
.panel{
  background:var(--panel);
  border:1px solid #50657a;
  border-radius:12px;
  padding:23px;
  margin:18px 0;
}
.stats{
  display:flex;
  justify-content:space-between;
  gap:12px;
  flex-wrap:wrap;
  padding:13px;
  border:1px solid #52657b;
  border-radius:9px;
}
.progress{
  height:9px;
  background:#3e5265;
  border-radius:9px;
  overflow:hidden;
  margin:12px 0;
}
.progress div{
  height:100%;
  background:var(--gold);
  width:0;
  transition:width .3s;
}
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:14px;
}
.evidence{
  background:#f1e6cf;
  color:#252525;
  border:2px solid #bd9b66;
  border-radius:8px;
  padding:16px;
}
.evidence h3{color:#703421;margin-top:0}
.evidence p{margin-bottom:0}
.question{
  border-top:1px solid #52657a;
  padding:22px 0;
}
.question:first-child{border-top:0}
.option{
  display:block;
  width:100%;
  text-align:left;
  margin:9px 0;
  background:#283d53;
}
.option.chosen{border:2px solid var(--gold)}
.option.correct{
  border:2px solid #85e3a0;
  background:#214d3b;
}
.option.wrong{
  border:2px solid #ff8490;
  background:#602d38;
}
.explanation{
  padding:14px;
  background:#122536;
  border-left:4px solid var(--gold);
  margin-top:12px;
  border-radius:4px;
}
.hidden{display:none!important}
.actions{
  display:flex;
  gap:12px;
  flex-wrap:wrap;
  margin:22px 0;
}
textarea{
  width:100%;
  min-height:130px;
  padding:13px;
  background:#f7f3e9;
  color:#172638;
  border-radius:7px;
}
label{display:block;margin:15px 0 7px;font-weight:bold}
.notice{color:var(--muted);font-size:14px}
#feedback{margin-top:16px}
@media print{
  body{background:white;color:black}
  header,.stats,.actions,.progress,.game-only{display:none!important}
  .panel{background:white;color:black;border:1px solid #888}
  h2,h3{color:black}
  textarea{color:black}
}
@media(max-width:600px){
  main{padding:12px}
  .panel{padding:16px}
}
</style>
</head>

<body>
<header>
  <div class="eyebrow">Blackwood Police Department</div>
  <h1>Murder at Blackwood Manor</h1>
  <p class="subtitle">
    Case File 014 | An Interactive Criminal Law Investigation
  </p>
</header>

<main>
<div class="stats game-only">
  <span id="stageLabel">Case briefing</span>
  <span id="scoreLabel">Score: 0</span>
</div>
<div class="progress game-only">
  <div id="progressBar"></div>
</div>

<section id="intro" class="panel">
  <div class="eyebrow">Confidential case briefing</div>
  <h2>A Death at Blackwood Manor</h2>

  <p>
    At 10:42 PM, police received an emergency call
    reporting an unconscious man at Blackwood Manor.
  </p>

  <p>
    The victim, wealthy property developer
    <strong>Edward Blackwood</strong>, was discovered
    in his private study with a fatal head injury.
    Investigators recovered a bloodstained bronze
    bookend near his body.
  </p>

  <p>
    Three people were at the estate that evening.
    Each had a possible motive. But motive alone
    cannot establish criminal guilt.
  </p>

  <h3>Your Assignment</h3>
  <p>
    Investigate the evidence, evaluate the legality
    of police procedures, analyze potential criminal
    charges, and decide whether the available
    evidence supports a conviction.
  </p>

  <p>
    You will complete five stages and answer
    17 legal review questions.
    Each correct answer earns 10 points.
  </p>

  <button class="primary" id="startBtn">
    Open Case File
  </button>
</section>

<section id="game" class="hidden">
  <div class="panel">
    <div class="eyebrow" id="stageNumber"></div>
    <h2 id="stageTitle"></h2>
    <p id="stageDescription"></p>
  </div>

  <div id="evidenceArea" class="grid"></div>

  <section class="panel">
    <h2>Legal Analysis Challenge</h2>
    <div id="questionsArea"></div>
    <div id="feedback" aria-live="polite"></div>
  </section>

  <div class="actions">
    <button class="primary" id="nextBtn" disabled>
      Continue Investigation
    </button>
  </div>
</section>

<section id="finalReport" class="panel hidden">
  <div class="eyebrow">Investigation complete</div>
  <h2>Final Case Report</h2>
  <p id="finalScore"></p>
  <p id="performance"></p>

  <h3>Final Case Assessment</h3>
  <p>
    The evidence points most strongly toward
    <strong>Daniel Mercer</strong>, but identifying
    a likely suspect is not the same as proving
    every element of a homicide offense beyond
    a reasonable doubt.
  </p>

  <p>
    The investigation also raises questions about
    the admissibility of evidence and the
    reliability of witness statements.
  </p>

  <label for="reflection1">
    1. Which evidence most strongly supports
    your conclusion, and why?
  </label>
  <textarea id="reflection1"
    placeholder="Explain your reasoning..."></textarea>

  <label for="reflection2">
    2. What additional evidence would you need
    before recommending a criminal charge?
  </label>
  <textarea id="reflection2"
    placeholder="Identify gaps in the investigation..."></textarea>

  <label for="reflection3">
    3. What constitutional issue could affect
    the prosecution's case?
  </label>
  <textarea id="reflection3"
    placeholder="Apply the relevant legal standard..."></textarea>

  <div class="actions game-only">
    <button class="primary" onclick="window.print()">
      Print Case Report
    </button>
    <button id="restartBtn">Restart Investigation</button>
  </div>

  <p class="notice">
    This is a fictional educational case. Legal
    standards are presented primarily from a
    general U.S. criminal-law perspective.
    State procedures and offense definitions vary.
    Results are not automatically sent to Canvas.
  </p>
</section>
</main>

<script>
// ======================================
// INSTRUCTOR EDITING AREA
// Change questions, answers, and evidence.
// correct is the zero-based answer index.
// ======================================

const stages = [
{
 title:"The Crime Scene",
 description:"Examine the physical evidence and determine which legal concepts apply.",
 evidence:[
  ["Medical Examiner",
   "Edward Blackwood died from blunt-force trauma to the head. The injury is consistent with the bronze bookend."],
  ["Study Door",
   "The door was closed but unlocked. There was no visible damage to the lock."],
  ["Crime Scene",
   "Investigators photographed the room before collecting the bookend and other evidence."]
 ],
 questions:[
  {
   q:"Which term describes the prohibited physical conduct required for a criminal offense?",
   options:["Mens rea","Actus reus","Voir dire","Habeas corpus"],
   correct:1,
   why:"Actus reus refers to the prohibited conduct or legally required act element of a crime."
  },
  {
   q:"What is the prosecution's burden of proof at a criminal trial?",
   options:["Reasonable suspicion","Preponderance of evidence","Beyond a reasonable doubt","Probable cause"],
   correct:2,
   why:"The prosecution must prove each element of the charged offense beyond a reasonable doubt."
  },
  {
   q:"Why should investigators document evidence before moving it?",
   options:["To guarantee conviction","To preserve context and support evidence integrity","To eliminate the need for witnesses","To establish motive automatically"],
   correct:1,
   why:"Documentation helps preserve the scene's original condition and supports the reliability of later analysis."
  }
 ]
},
{
 title:"The Suspect Interviews",
 description:"Review the three people who were present at the manor.",
 evidence:[
  ["Daniel Mercer — Business Partner",
   "Daniel argued with Edward about missing company funds. A camera shows him near the study corridor at 10:10 PM."],
  ["Clara Blackwood — Spouse",
   "Clara recently learned Edward planned to change his estate documents. She says she remained in the dining room."],
  ["James Holloway — Groundskeeper",
   "James was dismissed earlier that week. He says he was repairing a garden gate when the injury occurred."],
  ["Witness Statement",
   "A housekeeper recalls hearing an argument but cannot reliably identify either speaker."]
 ],
 questions:[
  {
   q:"Which statement about motive is legally accurate?",
   options:["Motive alone proves guilt","Motive is always a required element","Motive may be relevant but does not independently establish guilt","A suspect without motive cannot be charged"],
   correct:2,
   why:"Motive can be circumstantial evidence, but it is not generally an element of murder."
  },
  {
   q:"Which standard generally permits a brief investigative detention based on specific, articulable facts?",
   options:["Reasonable suspicion","Beyond a reasonable doubt","Clear and convincing evidence","Judicial notice"],
   correct:0,
   why:"Reasonable suspicion generally supports a brief Terry investigative detention."
  },
  {
   q:"Which standard is generally required for a lawful arrest?",
   options:["Mere suspicion","Probable cause","Proof beyond a reasonable doubt","A confession"],
   correct:1,
   why:"Probable cause requires facts supporting a reasonable belief that the person committed an offense."
  }
 ]
},
{
 title:"Constitutional Check",
 description:"Determine whether police investigative actions comply with constitutional protections.",
 evidence:[
  ["Daniel's Vehicle",
   "Without consent or a warrant, officers opened Daniel's locked vehicle to look for financial records. No immediate emergency was reported."],
  ["Interview Room",
   "Daniel was formally arrested, placed in an interrogation room, and questioned without Miranda warnings."],
  ["Evidence Log",
   "The bookend was sealed and labeled, but its transfer between two evidence technicians was not documented."]
 ],
 questions:[
  {
   q:"Which constitutional amendment primarily protects against unreasonable searches and seizures?",
   options:["First","Fourth","Sixth","Eighth"],
   correct:1,
   why:"The Fourth Amendment protects against unreasonable government searches and seizures."
  },
  {
   q:"What is the strongest initial concern with the vehicle search?",
   options:["All vehicle searches require warrants","The search may lack a valid exception to the warrant requirement","Police can search any suspect's property","Financial documents are never evidence"],
   correct:1,
   why:"Vehicle searches may be warrantless under recognized exceptions, but officers need a valid legal basis. The automobile exception generally requires probable cause."
  },
  {
   q:"When are Miranda warnings generally required?",
   options:["Before every police conversation","Before custodial interrogation","Only after indictment","Only when a suspect requests a lawyer"],
   correct:1,
   why:"Miranda warnings are generally required before custodial interrogation. An unwarned statement may be excluded from the prosecution's case-in-chief, subject to applicable doctrine."
  },
  {
   q:"What is the main concern with the missing evidence transfer record?",
   options:["It automatically proves innocence","It may create a chain-of-custody and reliability issue","It automatically dismisses the charges","It establishes self-defense"],
   correct:1,
   why:"A gap in chain-of-custody documentation can affect the foundation, admissibility, or weight of evidence, depending on the circumstances."
  }
 ]
},
{
 title:"Preparing for Trial",
 description:"Evaluate criminal charges and judicial procedures.",
 evidence:[
  ["Forensic Report",
   "Daniel's fingerprints were found on the bookend. He acknowledges handling it during a business meeting the previous week."],
  ["Digital Evidence",
   "A deleted message from Daniel reads: 'Edward cannot expose what happened.' The precise meaning remains disputed."],
  ["Timeline",
   "A security camera places Daniel in the study corridor shortly before the estimated time of death, but not inside the study."]
 ],
 questions:[
  {
   q:"What does mens rea refer to?",
   options:["The criminal act","The required mental state","The punishment","The jury's decision"],
   correct:1,
   why:"Mens rea refers to the culpable mental state required by the applicable criminal statute."
  },
  {
   q:"What is an indictment?",
   options:["A jury's guilty verdict","A formal charge issued by a grand jury","A sentencing recommendation","A defense motion"],
   correct:1,
   why:"An indictment is a formal accusation returned by a grand jury. Charging procedures vary by jurisdiction."
  },
  {
   q:"What is voir dire?",
   options:["Jury selection questioning","An appeal","A search procedure","A plea agreement"],
   correct:0,
   why:"Voir dire involves questioning prospective jurors to assess their qualifications and potential bias."
  },
  {
   q:"Which conclusion about Daniel's fingerprints is most legally defensible?",
   options:["They conclusively prove murder","They are irrelevant because Daniel had visited","They establish contact with the object but not necessarily when or why","They prove intent"],
   correct:2,
   why:"Fingerprint evidence may establish contact but does not, by itself, establish the timing, circumstances, or required mental state."
  }
 ]
},
{
 title:"Verdict and Review",
 description:"Evaluate the available evidence and the remaining procedural issues.",
 evidence:[
  ["Prosecution Theory",
   "The prosecution argues Daniel attacked Edward to prevent discovery of financial misconduct."],
  ["Defense Theory",
   "The defense argues the physical evidence has innocent explanations and the timeline leaves reasonable doubt."],
  ["Judicial Instructions",
   "The jury must evaluate the admissible evidence and decide whether every element of the charged offense has been proven beyond a reasonable doubt."]
 ],
 questions:[
  {
   q:"Which statement correctly describes a not-guilty verdict?",
   options:["It proves the defendant did nothing wrong","It means the prosecution failed to establish guilt beyond a reasonable doubt","It always means the police acted unlawfully","It prevents every future civil action"],
   correct:1,
   why:"An acquittal means the prosecution did not meet its burden of proof; it is not necessarily an affirmative finding of factual innocence."
  },
  {
   q:"What is the primary function of an appeal?",
   options:["To automatically retry every witness","To review alleged legal errors in the lower court","To select a new prosecutor","To determine whether police had a motive"],
   correct:1,
   why:"Appellate courts primarily review claimed legal errors under applicable standards of review."
  },
  {
   q:"Which approach best demonstrates sound criminal-law reasoning?",
   options:["Choose the suspect with the strongest motive","Assume suspicious behavior proves guilt","Evaluate each element, admissible evidence, and reasonable alternative explanations","Convict whenever there is probable cause"],
   correct:2,
   why:"Criminal liability requires proof of the charged offense's elements, evaluated under the correct burden of proof."
  }
 ]
}
];

// ======================================
// GAME ENGINE
// ======================================

let currentStage=0;
let score=0;
let responses=[];
let answered=0;

const $=id=>document.getElementById(id);
const totalQuestions=stages.reduce(
 (sum,stage)=>sum+stage.questions.length,0
);

function createElement(tag,text,className){
 const element=document.createElement(tag);
 if(text!==undefined)element.textContent=text;
 if(className)element.className=className;
 return element;
}

function startGame(){
 currentStage=0;
 score=0;
 responses=[];
 $("intro").classList.add("hidden");
 $("finalReport").classList.add("hidden");
 $("game").classList.remove("hidden");
 loadStage();
}

function loadStage(){
 answered=0;
 const stage=stages[currentStage];

 $("stageNumber").textContent=
  "Investigation Stage "+(currentStage+1)+" of "+stages.length;
 $("stageTitle").textContent=stage.title;
 $("stageDescription").textContent=stage.description;
 $("stageLabel").textContent=stage.title;
 $("scoreLabel").textContent="Score: "+score;
 $("nextBtn").disabled=true;
 $("nextBtn").textContent=
  currentStage===stages.length-1
  ?"Complete Investigation"
  :"Continue Investigation";

 const evidenceArea=$("evidenceArea");
 evidenceArea.replaceChildren();

 stage.evidence.forEach(([title,description])=>{
  const card=createElement("article",undefined,"evidence");
  card.append(
   createElement("h3",title),
   createElement("p",description)
  );
  evidenceArea.appendChild(card);
 });

 const area=$("questionsArea");
 area.replaceChildren();
 $("feedback").textContent="";

 stage.questions.forEach((question,index)=>{
  const section=createElement("section",undefined,"question");
  const title=createElement(
   "h3",(index+1)+". "+question.q
  );
  section.appendChild(title);

  const choices=createElement("div");
  const explanation=createElement("div",undefined,"explanation hidden");

  question.options.forEach((option,optionIndex)=>{
   const button=createElement(
    "button",
    String.fromCharCode(65+optionIndex)+". "+option,
    "option"
   );
   button.type="button";

   button.addEventListener("click",()=>{
    if(section.dataset.answered)return;

    section.dataset.answered="true";
    answered++;

    const correct=optionIndex===question.correct;
    if(correct)score+=10;

    responses.push({
     stage:stage.title,
     question:question.q,
     selected:option,
     correct,
     explanation:question.why
    });

    [...choices.children].forEach((choiceButton,i)=>{
     choiceButton.disabled=true;
     if(i===question.correct)
      choiceButton.classList.add("correct");
     if(i===optionIndex&&!correct)
      choiceButton.classList.add("wrong");
    });

    explanation.classList.remove("hidden");
    explanation.replaceChildren(
     createElement(
      "strong",
      correct?"Correct!":"Review this concept:"
     ),
     createElement("p",question.why)
    );

    $("scoreLabel").textContent="Score: "+score;

    if(answered===stage.questions.length){
     $("nextBtn").disabled=false;
     $("feedback").textContent=
      "Stage complete. Continue when ready.";
    }
   });

   choices.appendChild(button);
  });

  section.append(choices,explanation);
  area.appendChild(section);
 });

 const completed=responses.length;
 $("progressBar").style.width=
  (completed/totalQuestions*100)+"%";
}

function nextStage(){
 if(answered!==stages[currentStage].questions.length)return;

 currentStage++;
 if(currentStage>=stages.length){
  finishGame();
 }else{
  loadStage();
  window.scrollTo({top:0,behavior:"smooth"});
 }
}

function finishGame(){
 $("game").classList.add("hidden");
 $("finalReport").classList.remove("hidden");
 $("stageLabel").textContent="Investigation complete";
 $("progressBar").style.width="100%";

 const max=totalQuestions*10;
 const percentage=Math.round(score/max*100);

 $("finalScore").textContent=
  "Final score: "+score+" / "+max+" ("+percentage+"%)";

 $("performance").textContent=
  percentage>=90
  ?"Outstanding legal analysis. Review the case and prepare your final reasoning."
  :percentage>=70
  ?"Good work. Review the explanations for any missed questions."
  :"Continue reviewing the relevant legal standards and consider replaying the investigation.";

 window.scrollTo({top:0,behavior:"smooth"});
}

$("startBtn").addEventListener("click",startGame);
$("nextBtn").addEventListener("click",nextStage);
$("restartBtn").addEventListener("click",()=>{
 $("reflection1").value="";
 $("reflection2").value="";
 $("reflection3").value="";
 startGame();
 window.scrollTo({top:0,behavior:"smooth"});
});
</script>
</body>
</html>
