# Snake
public partial class Form1 = Form
{   
  private list<circle>snake = new list<circle>();
  private Circle food = new Circle();
  
  public Form1()
  {
    InitializeComponenet();
    
    //set settings to defualt
    new Settings();
    
    //Set game speed and start timer
    gameTimer.Interval = 1000/Settings.Speed;
    gameTimer.Tick += UpdateScreen();
    gameTimer.Start();
    
    //Start New Game
    StartGame();
    
    }
    
    private void StartGame()
    {
    
      //Set settings to default
      new Settings();
      
      snake.Clear();
      circle head = new Circle();
      head.X = 10;
      head.Y = 5;
      snake.Add(head);
      
      LblScore.Text = Settings.Score.ToString();
      GenerateFood();
    }
    
    //Place Random food game
    private void GenerateFood()
    {
      int maxXPos = pbCanvas.size.width/Settings.Width;
      int maxYPos = pbCanvas.Size.Height/Settings.Height;
      
      Random random = new Random();
      food = new Circle();
      food.X = random.Next(0, maxXPos);
      food.Y = random.Next(0, maxYPos);
    }
}
