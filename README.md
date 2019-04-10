# PROCESSAMENTO DIGITAL DE IMAGENS










#include <iostream>
#include <opencv2/opencv.hpp>

using namespace cv;
using namespace std;

int main(int argc, char** argv){
  Mat image;
  int width, height, x1, x2, y1, y2;

  image = imread(argv[1],CV_LOAD_IMAGE_GRAYSCALE);

  width  = image.size().width;
  height = image.size().height;

  cout << "Digite X1 e Y1: ";
  cin >> x1;
  cin >> y1;

  if(x1 > height || y1 > width || x1 < 0 || y1 < 0){
    cout << "Coordenadas Invalidas.";
    return -1;
  }

  cout << "Digite X2 e Y2: ";
  cin >> x2;
  cin >> y2;

  if(x2 > height || y2 > width || x2 < 0 || y2 < 0){
    cout << "Coordenadas Invalidas.";
    return -1;
  }

  imshow("Imagem", image);
  waitKey();

  //INVERTE AS CORES ENTRE OS PONTOS DADOS.
  for(int i = x1; i < x2; i++)
	for(int j = y1; j < y2; j++)
	  image.at<uchar>(i,j) = 255 - image.at<uchar>(i,j);

  imshow("Imagem", image);
  imwrite("Regions.png", image);
  waitKey();

  return 0;
}


