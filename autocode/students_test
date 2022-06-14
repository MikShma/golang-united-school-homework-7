package coverage

import (
	"os"
	"reflect"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func Test_SetMatrix(t *testing.T) {
	matrix, _ := New("1 2 3\n" +
		"4 5 6 ")
	expectedMatrix := []int{1, 2, 3, 4, 5, 11}

	if !matrix.Set(1, 2, 11) {
		t.Errorf("could not set a new value")
	}

	if !reflect.DeepEqual(expectedMatrix, matrix.data) {
		t.Errorf("expected to get %v, but actual is %v", expectedMatrix, matrix.data)
	}
}

func Test_ColsMatrix(t *testing.T) {
	matrix, _ := New("1 2 3\n" +
		"4 5 6 ")
	actualCols := [][]int{
		0: {1, 4},
		1: {2, 5},
		2: {3, 6},
	}
	cols := matrix.Cols()
	if len(cols) != 3 {
		t.Errorf("the expected number of cols: 3, but actual %d", len(cols))
	}

	if len(cols[0]) != 2 || len(cols[1]) != 2 || len(cols[2]) != 2 {
		t.Errorf("the expected number of rows: 2, but actual %d and %d, %d", len(cols[0]), len(cols[1]), len(cols[2]))
	}

	if !reflect.DeepEqual(actualCols, cols) {
		t.Errorf("expected to get %v, but actual is %v", actualCols, cols)
	}
}

func Test_RowsMatrix(t *testing.T) {
	matrix, _ := New("1 2 3\n" +
		"4 5 6 ")
	actualRows := [][]int{
		0: {1, 2, 3},
		1: {4, 5, 6},
	}
	rows := matrix.Rows()
	if len(rows) != 2 {
		t.Errorf("the expected number of rows: 2, but actual %d", len(rows))
	}

	if len(rows[0]) != 3 || len(rows[1]) != 3 {
		t.Errorf("the expected number of lines: 2, but actual %d and %d", len(rows[0]), len(rows[1]))
	}

	if !reflect.DeepEqual(actualRows, rows) {
		t.Errorf("expected to get %v, but actual is %v", actualRows, rows)
	}
}

func Test_NewMatrix(t *testing.T) {
	matrix, actualErr := New("1 2 3\n" +
		"4 5 6 ")
	if matrix.rows != 2 || matrix.cols != 3 || len(matrix.data) != 6 {
		t.Errorf("the expected rows=2, cols=3 and len(data)=6, but actual %d - %d - %d", matrix.rows, matrix.cols, len(matrix.data))
	}

	if actualErr != nil {
		t.Errorf("Could not create matrix, error: %v", actualErr)
	}
}

func Test_NewMatrix_ErrRowLenth(t *testing.T) {
	_, actualErr := New("1 2 3 4\n" +
		"4 5 6")

	if actualErr == nil {
		t.Errorf("Difrent lenth of rows, but error has not been received")
	}
}

func Test_NewMatrix_ErrAtoi(t *testing.T) {
	_, actualErr := New("1 2 3 \n" +
		"4 5 A")

	if actualErr == nil {
		t.Errorf("Char in row, but error has not been received")
	}
}

func Test_Swap(t *testing.T) {
	Pers := People{
		{},
		{firstName: "aaa"},
		{},
		{firstName: "bbb"},
	}

	Pers.Swap(1, 3)
	if Pers[1].firstName != "bbb" || Pers[3].firstName != "aaa" {
		t.Errorf("Swap function did't work")
	}

}

func Test_Less(t *testing.T) {
	tData := []struct {
		Pers     People
		Expected bool
	}{
		{
			Pers: People{
				{
					birthDay: time.Now(),
				},
				{
					birthDay: time.Now().Add(time.Minute * 2),
				},
			},
			Expected: false,
		},
		{
			Pers: People{
				{
					birthDay: time.Now().Add(time.Minute * 2),
				},
				{
					birthDay: time.Now(),
				},
			},
			Expected: true,
		},
		{
			Pers: People{
				{
					firstName: "aaa",
					lastName:  "aaa",
				},
				{
					firstName: "aaa",
					lastName:  "bbb",
				},
			},
			Expected: true,
		},
		{
			Pers: People{
				{
					firstName: "aaa",
				},
				{
					firstName: "bbb",
				},
			},
			Expected: true,
		},
	}
	for k, v := range tData {
		got := v.Pers.Less(0, 1)
		if got != v.Expected {
			t.Errorf("[%d] expected: %t, got %t", k, v.Expected, got)
		}
	}

}

func Test_Len(t *testing.T) {
	tData := []struct {
		Pers     People
		Expected int
	}{
		{
			Pers: People{
				{
					firstName: "aaa",
					lastName:  "aaa",
					birthDay:  time.Now(),
				},
				{},
			},
			Expected: 2,
		},
		{
			Pers:     People{},
			Expected: 0,
		},
	}
	for k, v := range tData {
		got := v.Pers.Len()
		if got != v.Expected {
			t.Errorf("[%d] expected: %d, got %d", k, v.Expected, got)
		}
	}
}
