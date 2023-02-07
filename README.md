 <a href="?status=Accepted&id={{order.id}}" class="btn btn-success"><img src="/static/images/baseline_check_circle_black_24dp.png" width="23" height="23"></a>
<a href="?status=Rejected&id={{order.id}}" class="btn btn-danger"><img src="/static/images/baseline_delete_black_24dp.png" width="23" height="23"></a> {% endcomment %

@app.post("/Fregister",response_class=HTMLResponse)
def create_post(request:Request, name:str = Form(...),department:str = Form(...),contact_number:int = Form(...), date_of_birth:str = Form(...), email:str = Form(...), teachers_id:int = Form(...), password:str = Form(...), photo: UploadFile = File(...)):
   
    conn = sqlite3.connect("app.db")
    cursor = conn.cursor()    
    if cursor.execute("INSERT INTO addteachers (name, email, password, department, contact_number, date_of_birth, teachers_id, photo) VALUES (?, ?, ?, ?, ?, ?, ?, ?)", (name, email, password, department, contact_number, date_of_birth, teachers_id, file_path)):
   
        return templates.TemplateResponse("Fregister.html",{"request":request,"msg":"Account created successfully!!"})
    return templates.TemplateResponse("Fregister.html",{"request":request,"msg":"Unable to create account"})



    const dateInput = document.getElementById("date-input");
      const timeInput = document.getElementById("time-input");

     // add event listeners to the input fields
     dateInput.addEventListener("change", updateDateTime);
     timeInput.addEventListener("change", updateDateTime);

     // update the date and time based on the input fields

     function updateDateTime() 
     {
      var d = dateInput.value;
      var curr_date = d.getDate();
      var curr_month = d.getMonth() + 1; //Months are zero based
      var curr_year = d.getFullYear();
      console.log(`${curr_year}-${curr_month}-${curr_date}`);
      const date = curr_date;
      const time = timeInput.value;
      console.log(`Date and time selected: ${date} ${time}`);
     }