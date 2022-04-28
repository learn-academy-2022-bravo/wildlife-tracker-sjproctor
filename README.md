# Tracker App - Rails API 4/28/2022

Setup:
- rails new tracker-app -d postgresql -T
- added the remote from github
- initial commit to main
- added RSpec
- Student tracker - name and cohort
- rails g resource Student name:string cohort:string
- rails routes - tell you all the route details

Still need:
- CRUD
- http verbs
- RESTful - index, show, create, update, destroy

### Index
Controller
```ruby
def index
  students = Student.all
  render json: students
end
```
- get localhost:3000/students

### Show
Controller
```ruby
def show
  student = Student.find(params[:id])
  render json: student
end
```
- get localhost:3000/students/1

### Create
Controller
```ruby
def create
  student = Student.create(student_params)
  if student.valid?
    render json: student
  else
    render json: student.errors
  end
end

private
def student_params
  params.require(:student).permit(:name, :cohort)
end
```
- post localhost:3000/students

### Update
Controller
```ruby
def update
  student = Student.find(params[:id])
  student.update(student_params)
  if student.valid?
    render json: student
  else
    render json: student.errors
  end
end
```
- patch localhost:3000/students/4
