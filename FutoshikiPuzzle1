/**
 * FutoshikiPuzzle.java
 * This class sets up a partially filled Futoshiki puzzle with a selected amount of symbols. 
 * allows digits to be entered into a square and allows constraints to be added.
 * Numbers and symbols are also randomly generated. 
 * February 2019.
 * @author 184752
 */

import java.util.Random;

public class FutoshikiPuzzle
{
// declarations
    public int [][] grid;
    private int gridSize;
    private String[][] rowConstraint;
    private String[][] columnConstraint;
    Random rand = new Random();
    
// constructor
    public FutoshikiPuzzle(int gridSize)
    {
        this.gridSize = gridSize;
        rowConstraint = new String[gridSize][gridSize - 1];
        columnConstraint = new String[gridSize - 1][gridSize];
        grid = new int[gridSize][gridSize];
    }  
// set square method which allows a digit to be put into a square.
    public void setSquare(int row, int column, int inputNum) 
    {
        grid[row][column] = inputNum;
        
    }
// retunrs the square in grid.  
    public int getSquare (int row, int column)
    {
       return grid[row][column];
    }
 
// method to the get row contratint.
    public String getRowConstraint(int row, int column)
    {
        return rowConstraint[row][column];
    }
 
 // method that allows a constraing to be entererd between square and square to the to its right.
    public void setRowConstraint(int row, int column, String constraint)
    {
        rowConstraint[row][column] = constraint;
    }
    
// method getting the collum constraint
    public String getColumnConstraint(int row, int column)
    {
        return columnConstraint[row][column];
    }

// method setting the constaint between the square and the square below. 
    public void setColumnConstraint(int row, int column, String constraint)
    {
        columnConstraint[row][column] = constraint;
    }

//gets a random number between the entered min and max range. 
    public int randomNumRange(int min, int max)
    {   
        return rand.nextInt((max - min) + 1) + min;
    }
        
 
    public void generateGridSquare() 
    {
        int row = randomNumRange(0, 4);
        int column = randomNumRange(0, 4);
        // Generating a new array location while the current array location is populated
        while (grid[row][column] > 0) 
        {
            row = randomNumRange(0, 4);
            column = randomNumRange(0, 4);
        }
        // Chooses a number from 1 - 5 to set at the random grid location
        grid[row][column] = randomNumRange(1, 5);
    }

    public void generateConstraintSquare(String[][] constraintArray, 
            String[] symbols) 
    {
        // Generating the initial row/column indices
        int row = randomNumRange(0, constraintArray.length - 1);
        int column = randomNumRange(0, constraintArray[0].length - 1);
        // Regenerating them if there's a symbol already there
        while (constraintArray[row][column] != null) 
        {
            row = randomNumRange(0, constraintArray.length - 1);
            column = randomNumRange(0, constraintArray[0].length - 1);
        }
        // Generating a random symbol and putting it at that grid location
        int id = randomNumRange(0, symbols.length - 1);
        constraintArray[row][column] = symbols[id];
    }

// method to fill the puzzle with symbols
    public void fillPuzzle(int symbolsToPlace) 
    {
        // select how many symbols to place in grid
        // int symbolsToPlace = gridSize * 2;
        for (int i = 0; i < symbolsToPlace; i++) 
        {
            int symbolType = randomNumRange(0, 2);
            if (symbolType == 0) 
            {
                // Choosing a grid symbol
                generateGridSquare();
            } 
            else if (symbolType == 1) 
            {
                // Choosing a row constraint symbol
                String[] rowSymbols = {"<", ">"};
                generateConstraintSquare(rowConstraint, rowSymbols);
            } 
            else 
            {
                // Choosing a column constraint symbol
                String[] columnSymbols = {"^", "v"};
                generateConstraintSquare(columnConstraint, columnSymbols);
            }
        }
    }
    
public String lengthenString(String input, char filler) 
{
        int rightLength;
        if (gridSize > 9) 
        {
            rightLength = 2;
        } 
        else 
        {
            rightLength = 1;
        }

        String output = input;
        for (int i = 0; i < rightLength - input.length(); i++) 
        {
            output = filler + output;
        }

        return output;
    }

  
// method to display the grid 
public String displayGrid() 
    {
        String buffer = "";

        for (int i = 0; i < gridSize; i++) 
        {
            for (int j = 0; j < gridSize; j++) 
            {
                buffer += "-";
                buffer += lengthenString("-", '-');
                buffer += "- ";
            }

            buffer += "\n";

            for (int j = 0; j < gridSize; j++) 
            {
                buffer += "|";
                if (grid[i][j] > 0) 
                {
                    buffer += lengthenString(String.valueOf(grid[i][j]), ' ');
                } 
                else 
                {
                    buffer += lengthenString(" ", ' ');
                }
                buffer += "|";

                if (j < gridSize - 1) 
                {
                    if (getRowConstraint(i, j) != null) 
                    {
                        buffer += getRowConstraint(i, j);
                    } 
                    else 
                    {
                        buffer += " ";
                    }
                }
            }

            buffer += "\n";

            for (int j = 0; j < gridSize; j++) 
            {
                buffer += "-";
                buffer += lengthenString("-", '-');
                buffer += "- ";
            }

            buffer += "\n";

            if (i < gridSize - 1) 
            {
                for (int j = 0; j < gridSize; j++) 
                {
                    buffer += " ";
                    if (getColumnConstraint(i, j) != null) 
                    {
                        buffer += lengthenString(getColumnConstraint(i, j), ' ');
                    } 
                    else 
                    {
                        buffer += lengthenString(" ", ' ');
                    }
                    buffer += "  ";
                }
            }
            buffer += "\n";
        }
        return buffer;
    }
    
    
            
 // main method   

    public static void main(String[] args) 
    {
        FutoshikiPuzzle puzzle = new FutoshikiPuzzle(5);
        puzzle.fillPuzzle(5);
        System.out.println(puzzle.displayGrid());
    } 

}
