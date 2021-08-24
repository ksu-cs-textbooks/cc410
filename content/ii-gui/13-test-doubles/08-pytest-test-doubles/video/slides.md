---
type: "reveal"
hidden: true
---
<section>
    <h3>Add Mocks to Test Class</h3>
    <pre><code class="python">from unittest.mock import patch<br><br>
class TestClassroom:<br>
    # tests here</code></pre>
</section>
<section>
    <h3>Creating Fake Objects</h3>
    <pre><code class="python stretch" style="font-size: 30px">from unittest.mock import patch
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom<br><br>
class TestClassroom:<br>
    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_classroom_has_teacher(self, fake_person, fake_teacher) -> None:
        classroom: Classroom = Classroom()
        assert classroom.has_teacher == False<br>
        classroom.add_teacher(fake_teacher)
        assert classroom.has_teacher == True 
    </code></pre>
</section>
<section>
    <h3>Adding a Method Stub</h3>
    <pre><code class="python stretch" style="font-size: 29px">@patch('people.Teacher', spec=Teacher)
@patch('people.Person', spec=Person)
def test_classroom_get_teacher_name(self, fake_person, fake_teacher) -> None:
    # create a method stub for `get_name` method
    fake_teacher.get_name.return_value = "Teacher Person"<br>
    classroom: Classroom = Classroom()
    classroom.add_teacher(fake_teacher)<br>
    # assert that the classroom returns the teacher's name
    assert classroom.get_teacher_name() == "Teacher Person"
    </code></pre>
</section>
<section>
    <h3>Adding a Property Stub</h3>
    <pre><code class="python stretch" style="font-size: 29px">@patch('people.Teacher', spec=Teacher)
@patch('people.Person', spec=Person)
def test_classroom_get_teacher_name(self, fake_person, fake_teacher) -> None:
    # create a property stub for `get_name` property
    type(fake_teacher).name = PropertyMock(return_value="Teacher Person")<br>
    classroom: Classroom = Classroom()
    classroom.add_teacher(fake_teacher)<br>
    # assert that the classroom returns the teacher's name
    assert classroom.get_teacher_name() == "Teacher Person"
    </code></pre>
</section>
<section>
    <h3>Static Classes</h3>
    <pre><code class="python stretch" style="font-size: 26px">@patch('people.Teacher', spec=Teacher)
@patch('people.Person', spec=Person)
def test_teacher_fails_minimum_age_requirement(self, fake_person, fake_teacher) -> None:
    # create a fake version of the static method
    with patch.object(TeacherRules, 'get_minimum_age', return_value=16):<br>
        # Add a fake property to the teacher
        type(fake_teacher).age = PropertyMock(return_value=15)
        classroom: Classroom = Classroom()<br>
        with pytest.raises(ValueError):
            classroom.add_teacher(fake_teacher)
        </code></pre>
</section>
