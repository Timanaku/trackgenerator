import random
import math
import numpy as np
import matplotlib.pyplot as plt


class TrackGenerator:
    def __init__(self, min_radius=5, max_radius=15, max_angle=math.pi / 4):
        self.min_radius = min_radius
        self.max_radius = max_radius
        self.max_angle = max_angle
        self.track = None

    def generate_track(self, num_points=15):
        # Initialize variables
        self.track = np.zeros((num_points, 2))
        center = np.array([0, 0])
        radius = self.min_radius + (self.max_radius - self.min_radius) * np.random.random()
        num_angles = num_points  # number of angles
        start_angle = 0  # starting angle in radians
        end_angle = 2 * np.pi  # ending angle in radians
        angles = np.linspace(start_angle, end_angle, num_angles, endpoint=False).tolist()

        # Generate points
        for i in range(num_points):
            point = center + radius * np.array([math.cos(angles[i]), math.sin(angles[i])])
            self.track[i] = point

            # Update center and radius
            center = point
            radius = self.min_radius + (self.max_radius - self.min_radius) * np.random.random()

        # Add noise
        self.track += 10 * np.random.normal(0, 0.1, self.track.shape)
        self.track -= 15 * np.random.normal(0, 0.1, self.track.shape)

        # Connect last point to first point
        self.track[-1] = self.track[0]

    def plot_track(self):
        if self.track is None:
            raise ValueError("No track generated yet!")
        plt.plot(self.track[:, 0], self.track[:, 1])
        plt.show()


def main():
    # Create a track generator
    track = TrackGenerator()
    # Generate a track
    track.generate_track()
    # Plot the track
    track.plot_track()


if __name__ == '__main__':
    main()
